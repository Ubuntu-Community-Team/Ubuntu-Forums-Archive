---
title: "question on script"
date: 2010-05-26
forum: The Cafe
---

### Post by holocene on 2010-05-26
how do I get a list of all users in /etc/passwd into a variable that I can iterate through. Reason: I want to do something based on the value of each user. 

For example, if my list of users was $userlist, then I want to do something like this:

for myuser in $userlist
  do
     some work here on $myuser
 done

I know I can use cut like this
cat /etc/passwd | cut -f1 -d: 
which gives me one user per line.

but how do I get it into a variable? 

for instance, this does not work
userlist=(cat /etc/passwd | cut -f1 -d:)

Thanks in advance. Sorry if this is not the right forum.
Steve.

---

### Post by lostinxlation on 2010-05-26
If you want to do something only in that foreach loop, this works too.
 
 
```

#!/bin/csh
 
foreach tmp (`cat /etc/passwd | sed -e 's/:.*$//' `)
   echo $tmp
end

```
 
 
If you really want to put them into a variable, do like
 
```

#!/bin/csh
 
set x = `cat /etc/passwd | sed -e 's/:.*$//' `
 
foreach tmp ($x)
    echo $tmp
end

```
 
NOTE: Above code is based on C shell, not a Bourne Shell variant.  I'd guess you can do the similar thing with bash.

---

### Post by holocene on 2010-05-27
lostinxlation,

Thanks for the response.

Based on your csh hint, I got it to work in bash like this

myusers=$(cat /etc/passwd | sed -e 's/:.*$//' )

for username in $myusers
    do    
        echo "this iteration is $username"
    done

Great forum.
Steve.

---

