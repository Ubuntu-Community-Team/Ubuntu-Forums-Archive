---
title: "system info script"
date: 2012-07-23
forum: Server Platforms
---

### Post by Loki57701 on 2012-07-23
I'm not sure this in the right place, but I didn't see a shell scripting specific forum.

I'm writing a system info script, and I'm having a problem with one particular part. 

I'm trying to get the systems processor using:

```
cat /proc/cpuinfo | awk '/model name/ {print $4, $5, $6, $7, $8}'
```

Which returns:

```
Intel(R) Celeron(R) D CPU 3.33GHz
```

It's not absolutely necessary, but I'd like to remove the (R)'s if possible - I'm picky.

I've done some experimenting with cut and grep, but I couldn't find anything that worked. 

Does anyone have a suggestion?

Thx

---

### Post by Toz on 2012-07-23
I'm certain it can be done in awk, but I'm not an awk'er. You could do it with sed like this:
```
cat /proc/cpuinfo | awk '/model name/ {print $4, $5, $6, $7, $8}' | sed -e 's/.R.//g'
```

---

### Post by steeldriver on 2012-07-23
The awk equivalent would be 'gsub' I think,

```
cat /proc/cpuinfo | awk '/model name/ {gsub(/\(R\)/,""); print $4, $5, $6, $7, $8}'
```or if you want to replace anything enclosed by parentheses such as (TM) as well as (R), you could try

```
cat /proc/cpuinfo | awk '/model name/ {gsub(/\([^)]+\)/,""); print $4, $5, $6, $7, $8}'
```

---

### Post by Loki57701 on 2012-07-23
Thank you very much for this!

I'll have to get more in depth with awk and sed. I wasn't even aware of gsub.

```
{gsub(/\(R\)/,"")
```
and 
```
{gsub(/\([^)]+\)/,"")
```

Are a complete mystery to me.. lol.

---

### Post by steeldriver on 2012-07-23
The regex syntax is essentially the same whether you do the actual match in awk or sed, unfortunately yes it does look like an explosion in a punctuation factory,  but basically /.../ are the regular expression delimiters (which you already know about), then

```
\(...\)
``` are literal parentheses and

```
[^)]+
``` means one or more characters excluding right parenthesis so

```
\([^)]+\)
``` is a non-greedy way to match any non-empty sequence of characters between parentheses

---

