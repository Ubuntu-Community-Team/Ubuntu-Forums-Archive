---
title: "someone help me with a bit of bash?"
date: 2010-04-25
forum: The Cafe
---

### Post by andru183 on 2010-04-25
some of my friends are thinking of getting into ubuntu and i said id make some bash shells to help em with some things, im only at bash 3 days tho and not good and cant get this firewall script to run

chmod +x is already done so it must be with the code

#!/bin/bash
echo 'Your chance to turn your fire wall on/off or check status
==========================================================================

Please type on/off or status'

read x

if x=on
m= enable
fi

if x=off
m= disable
fi

if x= status
m= status
fi

command sudo ufw -$m

think it runs but it just closes after it dose, if it dose run how to i get it to stay open till they press enter or sumit?

---

### Post by RiceMonster on 2010-04-25
try this:

```
#!/bin/bash
echo 'Your chance to turn your fire wall on/off or check status
================================================== ========================

Please type on/off or status'

read x

case "$x" in
	on)
		m="enable"
	;;
	off)
		m="disable"
	;;
	status)
		m="status"
	;;
	*)
	        echo "Invalid option! please enter on/off or status"
	        exit 1
esac

sudo ufw -$m

```

---

### Post by Xbehave on 2010-04-25
When reading a varialbe in bash you need to prepend it with $ (e.g $x)
It's also good practice to make it safe by putting "quotes" around it so that it is always read as a single token (e.g "$x")

The other change that ricemonster made was changing if... for a [case/esac]("http://en.wikipedia.org/wiki/Switch_statement"), that wasn't necessary but makes the code more readable.

I think ricemonster dropped the command at the end too, so the code should be (dammit got ninja'd)

```
#!/bin/bash
echo 'Your chance to turn your fire wall on/off or check status
================================================== ========================

Please type on/off or status'

read x

case "$x" in
	on)
		m="enable"
	;;
	
	off)
		m="disable"
	;;
	status)
		m="status"
	;;
	*)
	        echo "Invalid on/off status!"
	        exit 1;
[COLOR="Red"]        ;; #you'll never get here but if you ever change the code it's best to have you case closed[/COLOR]
esac

[COLOR="Red"]sudo ufw -"$m"[/COLOR]
```

---

### Post by RiceMonster on 2010-04-25
> **Xbehave said:**
> p.s ricemonster heres an optimised version of your sig :P
```
yes Xbehave
```

lol. Yeah, my sig used to be "yes RiceMonster", but my current one spams the whole screen rather than printing new lines :p.

Also yes, it's probably a good idea to add the two semi colons at the end.

---

### Post by swoll1980 on 2010-04-25
Would x be user input in this script? I'm guessing read might be looking for user input, and case seems like it starts some kind of if/else logic. I'm trying to learn how to read bash scripts for school.

---

### Post by andru183 on 2010-04-25
sexy stuff guys, i am goina keep working at these and find out what these case things mean and stuff, just wanted to get some stuff goin, thanks verry much

---

### Post by andru183 on 2010-04-25
> **swoll1980 said:**
> Would x be user input in this script? I'm guessing read might be looking for user input, and case seems like it starts some kind of if/else logic. I'm trying to learn how to read bash scripts for school.

i dose, (now my knowledge isn't vast but the way i understand it) it looks for input to be typed and that can be used as a var and called later if needed

---

### Post by andru183 on 2010-04-25
@xbehave

the shell still closes before an answer is sent after status

---

### Post by RiceMonster on 2010-04-25
> **andru183 said:**
> @xbehave

the shell still closes before an answer is sent after status

I'm not following what you mean. It will prompt for their input once, check once, and then run the ufw command. Do you want it to prompt them again after they enter an answer once?

---

### Post by andru183 on 2010-04-25
> **RiceMonster said:**
> I'm not following what you mean. It will prompt for their input once, check once, and then run the ufw command. Do you want it to prompt them again after they enter an answer once?

no but if they ask for status to see if its on or not i wanted the shell to show the status, i thought the shell wouldn't close till the user either pressed ctrl-z or enter, didnt know it required something to stay open while it showed the status

---

### Post by juancarlospaco on 2010-04-25
OMG use Gufw

---

### Post by CharlesA on 2010-04-25
You could ask it to pause or sleep, but it would be simpler to just use GUFW.

---

### Post by RiceMonster on 2010-04-25
> **andru183 said:**
> no but if they ask for status to see if its on or not i wanted the shell to show the status, i thought the shell wouldn't close till the user either pressed ctrl-z or enter, didnt know it required something to stay open while it showed the status

With this code, it will keep going until they type "quit". If you want it to exit after any of the options, just add exit or break to said option.

```

#!/bin/bash

echo 'Your chance to turn your fire wall on/off or check status
================================================== ========================

Please type on/off or status'


while true; do

	read x

	case "$x" in
		on)
			sudo ufw -enable
		;;
		off)
			sudo ufw -disable	
		;;
		status)
			sudo ufw -status
		;;
		quit)
			echo "Bye!"
			exit
		;;
		*)
			echo "Invalid option"
		;;
        esac

done

```

---

### Post by swoll1980 on 2010-04-25
I don't get how Rice's sig works.
```
while true; do echo -n "RiceMonster "; done
```
While what is true? How does the script run if there is no value that is true?

---

### Post by Xbehave on 2010-04-25
> **swoll1980 said:**
> I don't get how Rice's sig works.
```
while true; do echo -n "RiceMonster "; done
```
While what is true? How does the script run if there is no value that is true?
while true is true (i.e this is always going to happen) write his name to the screen, this program will continue looping until it is killed.

---

### Post by RiceMonster on 2010-04-25
> **swoll1980 said:**
> I don't get how Rice's sig works.
```
while true; do echo -n "RiceMonster "; done
```
While what is true? How does the script run if there is no value that is true?

It's possible n pretty much every language, and it means the loop will run until either the loop is broken out of, or the program is killed. like XBehave said, true will always be true.

---

### Post by andru183 on 2010-04-25
fancy stuff everybody thanks for you help, like i said i am going to learn more about bash and hopefully get better, very helpful stuff tho

---

### Post by andru183 on 2010-04-25
i did have to remove the dash's in front of enable, disable and status to get it to work in case anyone else tries that code, spot on other than that

---

### Post by RiceMonster on 2010-04-25
> **andru183 said:**
> i did have to remove the dash's in front of enable, disable and status to get it to work in case anyone else tries that code, spot on other than that

Sorry, I'm not familiar with ufw, so I didn't know the exact syntax. My mistake.

---

### Post by andru183 on 2010-04-25
> **RiceMonster said:**
> Sorry, I'm not familiar with ufw, so I didn't know the exact syntax. My mistake.

no worries, you did do everything else for me, i don't mind have to take out a dash after that

---

### Post by iponeverything on 2010-04-26
no if's just:
```

echo {R,R}{i,i}{c,c}{e,e}{M,M}{o,o}{n,n}{s,s}{t,t}{e,e}{r,r}

```

---

