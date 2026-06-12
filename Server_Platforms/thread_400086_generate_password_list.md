---
title: "generate password list"
date: 2007-04-03
forum: Server Platforms
---

### Post by uric on 2007-04-03
Hi, 

I am testing the security on a network. I wonder if there is a easy way to generate a password list? I know the first four letters and I know that there are two digets in the end, I need to generate a password list with all possible combinations, uppercase, lowercase.

lets say the password is:

      full???85

the first four letters are right but dont know if they are uppercase or lowercase.

the ??? means there could be up to 3 random letters here .

the number 8 and 5 are two random digets.


I am going to use the list with THC Hydra 5.3

Thanks

---

### Post by foxylad on 2007-04-04
This task is just complex enough that awk or sed would not work. I like Python, but you might want to use Perl or some other language.

Cheers!
Greg.

---

### Post by uric on 2007-04-04
hmm... Python... no
Perl ... no
other language ....  hmm

would english work? :D

---

### Post by wieman01 on 2007-04-04
I suggest you use a commercial password list:

[http://www.openwall.com/]("http://www.openwall.com/")

The commercial version found on the website include over 40 million passwords in 20 different languages with special characters and upper & lower case. Very useful and save you a lot of time.

_**EDIT:**_
There is also free version available with roughly 4 million entries. Good for a start I guess.

---

### Post by craigp84 on 2007-04-04
Depending on how much compute you have, and how beefy the compute running the service you wish to attack is, this could take weeks.

4 x Chars, Upper and Lower Case = 2^4 = 16
  ... multiplied by ...
Up to 3 Chars, Upper and Lower Case = (52^3 + 52^2 + 52) = 143,364
  ... multiplied by ...
2 x digits = 10^2 = 100

Total = 229,382,400 Permutations

This list would require approx (229,382,400 * 10) = 2,293,824,000 bytes of storage. Or 2.1Gb or disk space.

But, i hope the below helps you out!

--- genpw.pl


#!/usr/bin/perl
#
# genpw.pl
# Craig Perry
# 4th Apr 2007
#
# Generate a PW list of a specific format.
#

use strict;

# Change to suit the first 4 letters, keep space seperated
my @first_four = qw/ f F /;
my @second_four = qw/ u U /;
my @third_four = qw/ l L /;
my @fourth_four = qw/ l L /;

my @alphabet = qw/ a b c d e f g h i j k l m n o p q r s t u v w x y z
                   A B C D E F G H I J K L M N O P Q R S T U V W X Y Z /;

for my $four1 ( @first_four ){
for my $four2 ( @second_four ){
for my $four3 ( @third_four ){
for my $four4 ( @fourth_four ){
for my $letter1 ( @alphabet ) {
for my $letter2 ( @alphabet ) {
for my $letter3 ( @alphabet ) {

  # Generate digits from 00 to 99
  for my $tail_digit ( 0..99 ) {
    printf "%s%02d\n", $four1 . $four2 . $four3 . $four4 . $letter1 . $letter2 . $letter3, $tail_digit;
  }

}
}
}
}
}
}
}


--- end genpw.pl

All the best,

Craig

---

### Post by uric on 2007-04-04
man thats so cool, brilliant!  Thank you Craig!

I will make a try with one random letter first...

Thanks again!

---

