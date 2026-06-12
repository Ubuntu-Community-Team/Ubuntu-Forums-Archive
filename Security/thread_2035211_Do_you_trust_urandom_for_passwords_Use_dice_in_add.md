---
title: "Do you trust urandom for passwords? Use dice in addition."
date: 2012-07-30
forum: Security
---

### Post by timhalo on 2012-07-30
Lately I've had an interest in numbers, randomness and secure passwords.

I want to be able to generate a random password quickly but have something better than urandom alone. Maybe dice is the idea!? This script takes a four digit numeric input (roll 4 dice) and produces a password by grep'ing urandom twice, concatenating the results and inserting a random number in a random location.

I chose a 12 digit password and left out special characters because sites/services are not consistent in their password requirements. Instructions are in the script for changing it to produce longer passwords.

I don't know scripting much at all. So yeah I realize it could be made tighter. Also I've tried to write it in such a way (with comments) that others can see whats going on (for integrity).

Credit and References:
 
[LIST]
[*][Writing Shell Scripts]("http://linuxcommand.org/lc3_writing_shell_scripts.php") at linuxcommand.org
[*][BASH scripting: check for numeric values]("http://www.linuxquestions.org/questions/programming-9/bash-scripting-check-for-numeric-values-352226/#post3992301") at linuxquestions.org.
[*]I think I got the dev urandom tr fold head code from here, on ubuntuforums.org but I can't such a post again.
[*]man pages
[/LIST]
 
```

#!/bin/bash
# References
#      Learning scripts http://linuxcommand.org/lc3_writing_shell_scripts.php
#      Testing for input type http://www.linuxquestions.org/questions/programming-9/bash-scripting-check-for-numeric-values-352226/#post3992301


echo "
------------------------------------------------
This script takes a four digit numeric input and
produces a password by grep'ing urandom twice
concatenating the results and inserting a random
number in a random location.

Roll four die, type results and press enter.
"
read number

if ! [ "$number" -eq "$number" 2> /dev/null ]; then
    echo ; echo "Error. Input not numerical."
    exit 1

elif [ "$number" -gt "6666" ]; then
    echo ; echo "Error. Input > 6666."
    exit 1

elif [ "$number" -lt "1111" ]; then
    echo ; echo "Error. Input < 1111."
    exit 1

# Section1
else
    part1=$(cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 10 | head -n 6666 | grep . -n | grep -E ^$number:)
    part2=$(cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 10 | head -n 6666 | grep . -n | grep -E ^$number:)

# Section2
echo "------------------------------------------------
grep urandom and cut out line numbers:"
cut1=$(echo $part1 | cut -c 6-)
cut2=$(echo $part2 | cut -c 6-)
echo $cut1
echo $cut2
sleep 2s

# Section3
echo "------------------------------------------------
Trim down and concatenate:"
trim1=$(echo $cut1 | cut -c 1-5)
trim2=$(echo $cut2 | cut -c 6-10)
echo $trim1
echo $trim2
concat=$(echo $trim1$trim2)
echo $concat
sleep 2s

# Section4
echo "------------------------------------------------
Find random location to insert a random number"
shuf1=$(shuf -i 1-10 -n 1)
randnum1=$(cat /dev/urandom | tr -dc '0-9' | fold -w 2 | head -n 1)
echo "Location is $shuf1"
echo "Random number is $randnum1"
sleep 2s

# Section5
echo "------------------------------------------------
Characters before/after random number"
cuta=$(echo $concat | cut -c -$shuf1)
cutb=$(echo $concat | cut -c $shuf1-)
cutc=$(echo $cutb | cut -c 2-)
echo "Before: $cuta"
echo "After:  $cutc"
sleep 2s

# Section6
echo "------------------------------------------------
New password is:"
echo $cuta$randnum1$cutc

echo "------------------------------------------------"

##### Notes
# Why head 6666? If you use 4 die, the maximum value is 6666.
# fold 10, in the else section, produces 10 characters per each line (6666 lines).
#      This is just (uneducated) attempt to increase randomness, instead of, for example, fold 2.
# For a larger password, here is an example:
# 1. In Section1, for each urandom line, increase the fold value to, say 16.
# 2. In Section3 increase the cut range in trim1 to 1-8 and trim2 to 9-16.
# 3. In Section4 increase shuf range in shuf1 to 1-16.
# 4. In Section4 change fold value in randnum1 as desired. E.g. 3 for digit number; 4 for 4 and etc.
#         Could probably switch cat dev urandom to shuf method.
# If you want special characters in your password:
#      In Section1, change both instances of: tr -dc 'a-zA-Z0-9'
#      to: tr -dc 'a-zA-Z0-9-_!@#$%^&*()_+{}|:<>?='
# I think thats it.
fi

```

---

### Post by Cheesemill on 2012-07-30
I use pwgen to generate my passwords:
```
rob@precise:~$ pwgen 12
ooPun6ri2chu Aizi2DoCaiwe AiWixie6phah ooL3iPiegoon Chaeh5fooghe Hap1iew9xoow
aeCh7aechair koo5maeDepie ChaeCeeS6NiS jaliiV0aevei NooChae0aiju Aep9dahNg2th
maedahquu3Ei pe3laeShema4 boh9Fah5aeSh ai5aHe9eod9t Noh0gu8luphu ac4iz4wuTh4I
quuta8AeDoht aeng5ohzaWik iY6uawo2nohn Ohph4Iedaeng doedaphohs8J Iejai9Shiqu6
FighahFoon3i zo5Eerae2uxo kohya4Iy9Ohc ahTe6ier1Aep ieb9Aichaequ Uli0aevohsho
Weel5Reej7Wo Waw9becienei aht2Oothie7c jai2Jaf6ahJi ooNg7ohh1Quo Phei8aesheey
Aehoofai8eeG uvie9Rejucho thooraroo9Jo On9Ongohthie Sheiquee2ahp Iengo7aeFaiv
eihait0zeHai doh6reiSahX3 Ied2nash6ix8 Woot1xiechei uafooCheim7a Phae7aexae6i
Ohmoo6AiK8ie UaReNeiv8ro4 Aequah5sheeV eich1jeexeeS bie5maifooTh Ohgif0ahchee
OhKoFohquai3 ia8OS9aV0Mah oole5Poosh8o kahJ7EeFoofo uutheeH9eiko joh3HeiPee2m
dear1ieMeluk ughas9EiRu3O gah9iiShie2y eeghoh1Uocho Sei6too5EiBe ou1Dahgaa6oo
loo3ahSaevie dieShoo1ao5e Ceecoe9loo0c Eifeethieho7 iiMap1tinieN aePh7ieph4ee
Saep9aicuZei ce2Ai4ne6koh Lif5dohGhae5 Taen9Aesh8ph thi9ooToora5 Aib3anaiFidi
ii0deihu3Ut7 amaip6Un6Ier ir1eadel0ooS Nong0tha1aer eKei0taeghis SaiLoh9koos7
Iethee9xoh7O Fohsh5pho9qu Tusoh7leiphu opheeR6oZoi1 quu9Ohy4neol sieLeetho1ai
na8Beefe0ieb Eighahg6eewe Quah4cheaPh5 ienupahv3ieG zeNooz3eixee eidah6Jeing1
eida1PhaiN7e wie7XahGhiis iLeeZaixo0im ieFiehaiyah9 pheequ5ahRei eeba9oYoe6oo
Feipheesae8p eGai4kuy5fae aiPookie7ooj quee7Eem1ige Ooxie5iesa5a phai5ohfaeDo
cheijah1Xei3 mih5Ze9ohch2 quainapai4Sh EingiZai2Jit BouMah8zeeza zeihoo3Ailoo
Sebaexi4rinu aequ8thieJ7i Cheip3weniep eZoluca2veir ohr5MaeGheeL yeiCiem6paeM
```

---

### Post by thnewguy on 2012-07-30
When it comes to generating passwords I don't think you have to worry about the randomness of urandom. Really, you're making a nonesensical, long, semi-complex password, any attempt to brute-force it isn't going to be helped/hindered by the values coming out of urandom.

A little while back I wrote a similar tool to pwgen, if you'd like to look at the code (it's in C), here it is:

```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

char *Create_Random_Password(int pass_length)
{
   char *new_password;
   int index;
   int random;

   new_password = (char *) calloc(pass_length, sizeof(char));
   if (! new_password)
     return NULL;

   /* make up new password */
   for (index = 0; index < pass_length; index++)
   {
      random = rand() % 61;
      if (random < 26)
        new_password[index] = 'A' + random;
      else if (( random >= 26) && (random < 52) )
        new_password[index] = 'a' + (random - 26);
      else
        new_password[index] = '0' + (random - 52);
   }

   return new_password;
}


int main(int argc, char *argv[])
{
  char *my_password;
  int password_length = 8;

  if (argc == 2)
     sscanf(argv[1], "%d", &password_length);
 
  if (password_length < 4)
     password_length = 8;

  srand( time(NULL) );
  my_password = Create_Random_Password(password_length);
  if (my_password)
  {
     printf("%s\n", my_password);
     free(my_password);
  }
  else
    printf("Was unable to generate password.\n");
  return 0;
}


```

---

### Post by Hungry Man on 2012-07-30
Password randomness/ entropy is pretty irrelevant. There's serious diminishing returns there.

---

