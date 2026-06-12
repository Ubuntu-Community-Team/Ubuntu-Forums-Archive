---
title: "Need bit of help with this conky script"
date: 2017-08-25
forum: Ubuntu/Debian BASED
---

### Post by LastDino on 2017-08-25
Well, to keep long story short I've been trying to get something like a stock ticker in conky setup for last 2 months. Finally gave up and one day accidentally found this ready made script in our Ubuntu forums post your conky thread posted by someone lot more capable than me in somewhere around 2015. 
```
#! /bin/bash
# stock-conky.sh by livibetter 2010-08-17
# small modifications by Scott Hayes 2015-08-31
# Usage: stock-conky.sh <chart_small|chart_large|header|quote> [ticker symbol] [x y]

case "$1" in
  chart_small)
    wget -q "http://ichart.finance.yahoo.com/t?s=$2&lang=en-US&region=US" -O "/tmp/yahoo.finance.$2.png"
    echo "\${image /tmp/yahoo.finance.$2.png -p $3,$4 -s 192x96 -f 60}"
    ;;
  chart_large)
    wget -q "http://ichart.finance.yahoo.com/b?s=$2&lang=en-US&region=US" -O "/tmp/yahoo.finance.$2.png"
    echo "\${image /tmp/yahoo.finance.$2.png -p $3,$4 -s 512x288 -f 60}"
    ;;
  header)
    echo 'Symbol      Last  Change             Open    High     Low     Volume       Date    Time'
    ;;
  quote)
    wget -q "http://download.finance.yahoo.com/d/quotes.csv?s=$2&f=sl1d1t1c1ohgvp2&e=.csv" -O - | awk -F "\"*,\"*" '{
ticker = substr(substr($1, 2, length($1) - 1), 1, 8);

printf("${alignr 54}%7.2f", $2); # Last

if ($5 > 0)                    # Change colour
  printf("${alignr}${color green}")
else if ($5 < 0)
  printf("${alignr}${color #EE9A49}")
else 
  printf("${alignr}${color white}")

if ($5 == "N/A")               # Print Change
  printf("    ${color}N/A (   N/A) ")
else
  printf("%7.2f (%5.2f%%)$color", $5, $10)

printf("\n")
}'
    ;;
esac
```

I copy pasted this in .conkyrc file to see what out put it gives, but I get error saying

```
$ conky
conky: Syntax error (/home/owl/.conkyrc:2: unexpected symbol near '#') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.
conky: [string "..."]:138: attempt to index local 'settings' (a nil value)


```

There is only one place that symbol is there in script and I've tried number of combinations and it doesn't work. I'm guessing I would need to edit the script quite a lot too, but I'm not that skilled yet so need to ask for help here rather than possibility of losing more hair on my head for another 2 months and no output :D

All suggestions and help is appreciated. Please help me!

---

### Post by LastDino on 2017-08-26
Bump! 

*sadface*

---

### Post by vasa1 on 2017-08-26
Can you post the original link? Plus I'm not sure you can paste a bash script into conkyrc or conky.conf.

---

### Post by LastDino on 2017-08-26
> **vasa1 said:**
> Can you post the original link? Plus I'm not sure you can paste a bash script into conkyrc or conky.conf.

.....I'm having a feeling that I've done some really basic and stupid mistake here but oh well :D

Here is the original post link

[https://ubuntuforums.org/showthread.php?t=281865&page=2316&p=13348044#post13348044](https://ubuntuforums.org/showthread.php?t=281865&page=2316&p=13348044#post13348044)

I'm not that familiar with either scripting or conky, so please excuse me <.<'

---

### Post by LastDino on 2017-08-29
Okay, I've made a script file saying market.sh and put in the current .conky folder

Made one .conkyrc file named fin.conkyrc and kept this line in it

```
S&P/TSX ${execpi 15 ~/conky/market.sh quote ^GSPTSE}
```

Content of script is same one which was used before. But now I get this error

```
conky -c /home/owl/.conky/fin.conkyrc
conky: Syntax error (/home/owl/.conky/fin.conkyrc:1: '=' expected near '&') while reading config file. 
conky: Assuming it's in old syntax and attempting conversion.
conky: [string "..."]:138: attempt to index local 'settings' (a nil value)


```

What to do next? Or rather what other things I'm doing wrong?

---

