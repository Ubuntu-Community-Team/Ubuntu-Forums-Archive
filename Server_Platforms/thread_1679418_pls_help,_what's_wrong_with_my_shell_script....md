---
title: "pls help, what's wrong with my shell script..."
date: 2011-02-01
forum: Server Platforms
---

### Post by koori on 2011-02-01
I read PaulLove and JoeMerlino's Book(<<Beginning Unix>>)
and copied this script with vi below(1stscript.sh):

```
#!/bin/bash
echo "GUESS THE SECRET COLOR"

read COLOR
if [ $COLOR="PURPLE" ]
then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $COLOR"
fi

```then i run it and got this result:
> 
$ chmod +x 1stscript.sh
$ ./1stscript.sh
GUESS THE SECRET COLOR
ABC
CORRECT!
WHAT?!!!
....

is there any thing wrong with my script.
my platform is Ubuntu Server 64bit.

pls help, thanx!

---

### Post by |{urse on 2011-02-01
the if statement needs a ; and it's good practice to place your then at the end

#!/bin/bash
echo "GUESS THE SECRET COLOR"
read COLOR
if [ $COLOR="PURPLE" ] ; then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $COLOR"
fi

does that work?

---

### Post by koori on 2011-02-01
doesn't work correctly, it returened the same result...
is there any way to solve this problem?...

---

### Post by clasificados on 2011-02-01
> **koori said:**
> I read PaulLove and JoeMerlino's Book(<<Beginning Unix>>)
and copied this script with vi below(1stscript.sh):

```
#!/bin/bash
echo "GUESS THE SECRET COLOR"

read COLOR
if [ $COLOR="PURPLE" ]
then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $COLOR"
fi

```then i run it and got this result:


WHAT?!!!
....

is there any thing wrong with my script.
my platform is Ubuntu Server 64bit.

pls help, thanx!


what if you define the secret color first



#!/bin/bash
secret=PURPLE
echo "GUESS THE SECRET COLOR"
read COLOR
if [ $COLOR = $secret ] ; then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $secret"
fi

---

### Post by |{urse on 2011-02-01
*facepalm*

I must be getting sleepy lol

---

### Post by koori on 2011-02-01
> **clasificados said:**
> what if you define the secret color first



#!/bin/bash
secret=PURPLE
echo "GUESS THE SECRET COLOR"
read COLOR
if [ $COLOR = $secret ] ; then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $secret"
fi


nothing has changed...
well, does that mean my shell was broken?

---

### Post by lavinog on 2011-02-01
You just needed to put a space around the =:
```
#!/bin/bash
echo "GUESS THE SECRET COLOR"

read COLOR
if [ $COLOR = "PURPLE" ]
then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $COLOR"
fi

```

When doing comparisons, it is a good habit to use quotes around the variable:
```

if [ "$COLOR" = "PURPLE" ]

```

Also why say that the secret color is $COLOR when $COLOR is the users response?
```

GUESS THE SECRET COLOR
asdf
INCORRECT!! THE SECRET COLOR IS asdf

```
;)

Also, there is a programming section in the forums:
Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Development & Programming > Programming Talk
This would be a good place to get help with this sort of stuff.

---

### Post by koori on 2011-02-01
> **lavinog said:**
> You just needed to put a space around the =:
```
#!/bin/bash
echo "GUESS THE SECRET COLOR"

read COLOR
if [ $COLOR = "PURPLE" ]
then
echo "CORRECT!"
else
echo "INCORRECT!! THE SECRET COLOR IS $COLOR"
fi

```

When doing comparisons, it is a good habit to use quotes around the variable:
```

if [ "$COLOR" = "PURPLE" ]

```

Also why say that the secret color is $COLOR when $COLOR is the users response?
```

GUESS THE SECRET COLOR
asdf
INCORRECT!! THE SECRET COLOR IS asdf

```
;)

Also, there is a programming section in the forums:
Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Development & Programming > Programming Talk
This would be a good place to get help with this sort of stuff.

Thanx, the problem is solved and thank you for guiding me to the right place:)
but there is still one strange thing happened.
after i entered "./1stscript.sh" and enter an incorrect value it often return an error message below:

> 
$ ./1stscript.sh
GUESS THE SECRET COLOR
BLUE
./1stscript: line 7:[: =:] unary operator expected
YOUR GUESS WAS WRONG. THE SECRET COLOR IS <PURPLE>.


but if i output this message into file the error message was dissappeared:
> 
$ ./1stscript.sh > error.log
GUESS THE SECRET COLOR
YOUR GUESS WAS WRONG. THE SECRET COLOR IS <PURPLE>.


why...okay maybe i could bring this question into that place.

thank you:)

---

### Post by lavinog on 2011-02-01
Can you post the contents of the script you used?

---

