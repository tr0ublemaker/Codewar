#codewar OJ


###7ku 
Create a function that returns the name of the winner in a fight between two fighters.

Each fighter takes turns attacking the other and whoever kills the other first is victorious. Death is defined as having health <= 0.

Each fighter will be an Fighter object/instance which looks like this:

Both health and damagePerAttack (damage_per_attack for python) will be integers larger than 0. You can mutate the Fighter objects.

Python

    class Fighter(object):
        def __init__(self, name, health, damage_per_attack):
            self.name = name
            self.health = health
            self.damage_per_attack = damage_per_attack
            
Example:

      declareWinner(new Fighter("Lew", 10, 2), new Fighter("Harry", 5, 4), "Lew") => "Lew"

      // Python
      declare_winner(Fighter("Lew", 10, 2), Fighter("Harry", 5, 4), "Lew") => "Lew"

      Lew attacks Harry; Harry now has 3 health.
      Harry attacks Lew; Lew now has 6 health.
      Lew attacks Harry; Harry now has 1 health.
      Harry attacks Lew; Lew now has 2 health.
      Lew attacks Harry: Harry now has -1 health and is dead. Lew wins.
      
##5ku Two Joggers

Description

Bob and Charles are meeting for their weekly jogging tour. They both start at the same spot called "Start" and they each run a different lap, which may (or may not) vary in length. Since they know each other for a long time already, they both run at the exact same speed.

Illustration

Example where Charles (dashed line) runs a shorter lap than Bob:

Example laps

Task

Your job is to complete the function nbrOfLaps(x, y) that, given the length of the laps for Bob and Charles, finds the number of laps that each jogger has to complete before they meet each other again, at the same time, at the start.

The function takes two arguments:

The length of Bob's lap (larger than 0)
The length of Charles' lap (larger than 0)
The function should return an array containing exactly two numbers:

The first number is the number of laps that Bob has to run
The second number is the number of laps that Charles has to run
Examples

    nbr_of_laps(5, 3) # returns [3,5]
    nbr_of_laps(4, 6); # returns [3, 2]

####my solution
    def nbr_of_laps(x, y):
        min = x if x > y else y
        for i in xrange(min,0,-1):
            if x%i == 0 and y%i ==0:
                break       
        return [y/i, x/i] 
####good solution
1.

        def nbr_of_laps(x, y):
            lcm = x
            while lcm % x + lcm % y != 0:
                lcm += x
            return [lcm / x, lcm / y]
            
2.
  
        from fractions import gcd

        def nbr_of_laps(x, y):
            return (y / gcd(x,y), x / gcd(x,y))