---
title: "Conky: Facebook Notifications"
date: 2010-09-03
forum: The Cafe
---

### Post by dmillerw on 2010-09-03
(Not sure why this is marked as solved...but uh...)

I was bored, and was looking for a way to easily get Facebook notifications on Ubuntu, since I always have my conky visible, I figured that was a good place to start.

This requires [fbcmd]("http://fbcmd.dtompkins.com/installation") which is pretty easy to install, and I've found it to be rather useful.

Decided to just combined it all into a single script, rather messy, but it works.
```
#!/bin/bash

if [ "$1" = "message" ]
then
	msgcount=$(fbcmd NOTIFY | grep MESSAGES_UNREAD | grep -oE "[[:digit:]]{1,}")

	if [ "$msgcount" -eq "0" ]
	then
		echo No New Messages

	elif [ "$msgcount" -eq "1" ]
	then
		echo '${color white}'$msgcount'${color aaaaaa}' NEW MESSAGE
	else

		echo '${color white}'$msgcount'${color aaaaaa}' NEW MESSAGES
	fi

elif [ "$1" = "poke" ]
then
	pokecount=$(fbcmd NOTIFY | grep POKES | grep -oE "[[:digit:]]{1,}")

	if [ "$pokecount" -eq "0" ]
	then
		echo No One Has Poked You

	elif [ "$pokecount" -eq "1" ]
	then
		echo '${color white}'$pokecount'${color aaaaaa}' PERSON HAS POKED YOU
	else

		echo '${color white}'$pokecount'${color aaaaaa}' PEOPLE HAVE POKED YOU
	fi

elif [ "$1" = "notify" ]
then
	notifycount=$(fbcmd NOTICES unread | grep -c :title)

	if [ "$notifycount" -eq "0" ]
	then
		echo No New Notifications

	elif [ "$notifycount" -eq "1" ]
	then
		echo '${color white}'$notifycount'${color aaaaaa}' NEW NOTIFICATION
	else

		echo '${color white}'$notifycount'${color aaaaaa}' NEW NOTIFICATIONS
	fi

elif [ "$1" = "friend" ]
then
	friendcount=$(fbcmd NOTIFY | grep FRIEND_REQUESTS | grep -oE "[[:digit:]]{1,}")

	if [ "$friendcount" -eq "0" ]
	then
		echo No New Friend Requests

	elif [ "$friendcount" -eq "1" ]
	then
		echo '${color white}'$friendcount'${color aaaaaa}' NEW Friend Request
	else

		echo '${color white}'$friendcount'${color aaaaaa}' NEW Friend Requests
	fi

elif [ "$1" = "group" ]
then
	groupcount=$(fbcmd NOTICES unread | grep -c :title)

	if [ "$groupcount" -eq "0" ]
	then
		echo No New Group Invites

	elif [ "$groupcount" -eq "1" ]
	then
		echo '${color white}'$groupcount'${color aaaaaa}' NEW Group Invite
	else

		echo '${color white}'$groupcount'${color aaaaaa}' NEW Group Invites
	fi

elif [ "$1" = "events" ]
then
	eventscount=$(fbcmd NOTICES unread | grep -c :title)

	if [ "$eventscount" -eq "0" ]
	then
		echo No New Events

	elif [ "$eventscount" -eq "1" ]
	then
		echo '${color white}'$eventscount'${color aaaaaa}' NEW Event
	else

		echo '${color white}'$eventscount'${color aaaaaa}' NEW Events
	fi

else
	echo "Please state a command, [message,poke,notify,friend,group,events]"
fi

```

Simple script, but I felt like sharing them anyway.

Add to your conky like so...
```
${color white} $alignr FACEBOOK
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook notify}
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook poke}
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook message}
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook friend}
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook group}
${color aaaaaa} $alignr ${execpi 15 ~/.scripts/facebook events}
```
...and you're good.

---

### Post by pwnst*r on 2010-09-03
Good stuff, thanks!

---

### Post by spillin_dylan on 2010-09-03
I realize I could probably find this by wading through the Conky mega-thread, but what kind of script are you using for displaying the computer names & IP addresses of your local network?  I think I'd like to try something similar.

---

### Post by dmillerw on 2010-09-03
> **spillin_dylan said:**
> I realize I could probably find this by wading through the Conky mega-thread, but what kind of script are you using for displaying the computer names & IP addresses of your local network?  I think I'd like to try something similar.

```
#!/bin/bash
if ping -c1 -W1 $1> /dev/null; then
echo '${color white} $alignr '$2 - '${color aaaaaa} ONLINE ${color}'
echo '${color white} $alignr '$1'${color}'
else
echo '${color white} $alignr '$2 - '${color aaaaaa} OFFLINE ${color}'
echo '${color white} $alignr '$1'${color}'
fi
```

It's nothing special, but there you go...format is IP then Name

```
./ping.sh [IP] [NAME]
```

---

### Post by spillin_dylan on 2010-09-03
Oh, you're just pinging a preset list!  I thought there was some way you were actually getting a list of what is online at any given time.  Like, for instance, what you see on a router configuration page.  I guess as long as the computer's IP doesn't change on your network, then this should work good, too.

But thanks for the swift reply!

---

### Post by dmillerw on 2010-09-03
> **spillin_dylan said:**
> Oh, you're just pinging a preset list!  I thought there was some way you were actually getting a list of what is online at any given time.  Like, for instance, what you see on a router configuration page.  I guess as long as the computer's IP doesn't change on your network, then this should work good, too.

But thanks for the swift reply!

I actually hadn't thought of doing it that way...might have to look into that, but you're welcome.

---

### Post by castironpants on 2010-09-21
Will this handle Requests and Invitations?

---

### Post by fatality_uk on 2010-09-21
I have never or ever want to be poked digitally!
But nice script anyway.

---

### Post by dmillerw on 2010-11-14
Just bringing this back up (if I'm allowed to do so, that is)

---

### Post by wmarin on 2011-03-07
Like a charm ! Thanx
William

---

### Post by sbjaved on 2011-09-07
Thank you. Works beautifully.

---

