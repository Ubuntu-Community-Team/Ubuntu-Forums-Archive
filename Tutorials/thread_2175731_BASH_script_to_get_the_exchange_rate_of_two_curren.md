---
title: "BASH script to get the exchange rate of two currencies"
date: 2013-09-20
forum: Tutorials
---

### Post by GrouchyGaijin on 2013-09-20
```



#!/bin/bash
#by GrouchyGaijin
# I called this script exrate.


echo "This script is for getting the current exchange rate "
read -p "Enter the symbol of the currency you want to convert from. Ex: SEK " var1
read -p "Enter the symbol of the currency you want to convert to. Ex: USD  " var2
read -p "Enter the amount you want to convert: " var3


wget -q -O - "http://www.google.com/finance/converter?a=$var3&from=$var1&to=$var2"|grep "<div id=currency_converter_result>"|sed 's/<[^>]*>//g'
until false; do
    echo "Press R to run the script again  or Q to quit. "
    read x
    if [ "$x" = "R" ]; then
    exrate
    elif [ "$x" = "Q" ]; then
        echo "Going down"
        killall exrate      
        break   
fi 
    done


```

---

### Post by Christian Heinrichs on 2013-10-30
Might I suggest some slight modifications?
I noticed the Q and R commands not working properly, so I replaced "exrate" with "bash exrate" and "killall exrate" with "exit 0".
You also referred to the x variable in the if else statement as "$x" string, which was changed to $x.
Another suggested change is the use of other variable names, because var1 etc. sounds too generic.
The rest are just minor formatting changes.

Not trying to be picky. Hope you are okay with this.

```

#!/bin/bash
# by GrouchyGaijin
# I called this script exrate.


echo "This script is for getting the current exchange rate"
read -p "Enter the abbreviation of the currency you want to convert from. Ex: SEK " convfrom
read -p "Enter the abbreviation of the currency you want to convert to. Ex: USD " convto
read -p "Enter the amount you want to convert: " convamount

wget -q -O - "http://www.google.com/finance/converter?a=$convamount&from=$convfrom&to=$convto" | grep "<div id=currency_converter_result>" | sed 's/<[^>]*>//g'

until false; do
    echo "Press R to run the script again or Q to quit."
    read x
    if [ $x = "R" ]; then
        bash exrate
    elif [ $x = "Q" ]; then
        echo "Going down"
        exit 0 #killall exrate
        break
fi
    done

```

---

### Post by GrouchyGaijin on 2013-10-30
> **codingaround said:**
> Might I suggest some slight modifications?
I noticed the Q and R commands not working properly, so I replaced "exrate" with "bash exrate" and "killall exrate" with "exit 0".
You also referred to the x variable in the if else statement as "$x" string, which was changed to $x.
Another suggested change is the use of other variable names, because var1 etc. sounds too generic.
The rest are just minor formatting changes.

Not trying to be picky. Hope you are okay with this.


But of course - thank you!

---

### Post by GrouchyGaijin on 2013-10-30
What was not working with the Q and R commands?
They both work as they should on my system.

---

### Post by Christian Heinrichs on 2013-10-31
I start the script with "bash exchange". Entering "r" does nothing and when "R" is entered I get the error:
```
exchange: line 17: exrate: command not found
```

When you input "q" nothing happens. Writing "Q" works and the script exits, but still gives out the message:
```
exrate: no process found
```

Based on those facts I propose some changes.

Line 16:
```
if [ "$x" = "R" ]; then
```
to
```
if [[ "$x" = "R" || "$x" = "r" ]]; then
```

Line 18:
```
elif [ "$x" = "Q" ]; then
```
to
```
elif [[ "$x" = "Q" || "$x" = "q" ]]; then
```

---

### Post by GrouchyGaijin on 2013-11-01
Well obviously if you call the script  using[COLOR=#000000] [/COLOR]bash exchange trying to killall exrate will result in a no process found error. That is why I mentioned that I called the script exrate.  I put the script in my PATH and call it by typing exrate.
As for the lower case option - OK.

---

### Post by steeldriver on 2013-11-01
Some comments

1) rather than calling the script recursively, it would be more natural to put the thing you want done inside the loop - if you want to preserve the existing script structure you could simply define that as a *function*

```

function doit() {
read -p "Enter the abbreviation of the currency you want to convert from: " -ei "SEK" convfrom
read -p "Enter the abbreviation of the currency you want to convert to: " -ei "USD" convto
read -p "Enter the amount you want to convert: " -ei "1" convamount

wget -q -O - "http://www.google.com/finance/converter?a=$convamount&from=$convfrom&to=$convto" | grep "<div id=currency_converter_result>" | sed 's/<[^>]*>//g'
}

```

(I made the reads interactive so that instead of 'Ex. SEK' it actually pre-fills 'SEK' as the default value) and then instead of recursing, have a loop like
```

echo "This script is for getting the current exchange rate"
doit
while true; do
  doit
done

```

2) a case statement makes it easy to handle the x = Q or R input, and even to make it case-insensitive - something like

```

echo "This script is for getting the current exchange rate"
doit
while : ; do

read -p "Press R to run the script again or Q to quit. " -n1 x
  echo
  case "$x" in
    R|r) doit
    ;;
  
    Q|q) exit
    ;;
  
    *) echo "Please enter R or Q"
    ;;
  esac
done

```

(I made another suggestion about the read, using -n1 so it's a true key press rather than waiting for a newline - see 'help read')

---

### Post by GrouchyGaijin on 2013-11-01
you the man Steeldriver

---

### Post by Christian Heinrichs on 2013-11-02
> **GrouchyGaijin said:**
> Well obviously if you call the script  usingbash exchange trying to killall exrate will result in a no process found error. That is why I mentioned that I called the script exrate.  I put the script in my PATH and call it by typing exrate.

Yes, in your initial post you mentioned that you called the script exrate. But you did not say, that you put the script in your PATH environment variable.

---

### Post by GrouchyGaijin on 2013-11-02
Sorry my mistake - I didn't realize that much explanation was required.

---

### Post by Christian Heinrichs on 2013-11-02
> **GrouchyGaijin said:**
> I didn't realize that much explanation was required.

Is this meant offensive?

---

### Post by GrouchyGaijin on 2013-11-02
Actually it is the truth, but feel free to take it any way you like.

---

### Post by Christian Heinrichs on 2013-11-02
Okay, no offense taken then.

---

### Post by GrouchyGaijin on 2013-11-02
In any case, SteelDriver's solution is much better

---

### Post by Christian Heinrichs on 2013-11-02
> **GrouchyGaijin said:**
> In any case, SteelDriver's solution is much better
Well, it's becoming obvious that you are trying to provoke a negative kind of reaction from  me, therefore I am done responding to you.
Quite rude to become that offensive, after I suggested some minor modifications.

---

### Post by GrouchyGaijin on 2013-11-02
Whatever pal
I actually meant better than my script.

---

