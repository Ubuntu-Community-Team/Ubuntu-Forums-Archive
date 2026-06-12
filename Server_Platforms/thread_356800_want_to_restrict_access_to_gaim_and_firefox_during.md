---
title: "want to restrict access to gaim and firefox during homework"
date: 2007-02-08
forum: Server Platforms
---

### Post by haochela on 2007-02-08
Hello,

Does anyone have a solution for restricting program access by a specific user id during a particular time slot?

Specifically, I would like to restrict my daughter's access to instant messaging and web browsing during the hours of 6 and 8:30 so that she can focus on her homework.

If this post is more appropriately directed to another forum, please advise.

---

### Post by spin2cool on 2007-02-08
I'd write a small bash script to run that will change the permissions of the executables.  Then, set it to run at your desired times using a cron job.  There are lots of resources for cron around the web - it's not very hard to set up.

as for scripts, something like:

to disallow:
```
#!/bin/bash
chmod u-x /usr/bin/gaim
```

to allow:
```
#!/bin/bash
chmod u+x /usr/bin/gaim
```

Save them as *whatever*.sh, then set it up so that cron runs them as root at the times you want.

---

### Post by spin2cool on 2007-02-08
Oh, add another line to each script to restrict firefox

For what it's worth, restricting web access during homework time might be a bad idea - it's the biggest educational resource in the world.  :)

Of course, myspace isn't exactly a learning experience...

---

### Post by haochela on 2007-02-09
Thanks for the scripting idea! I had not thought of that! 

As for stopping web surfing, you do have a point. MySpace is the problem as it sucks a fair amount of her study time. OTOH if I were to restrict access to java during this time then she'd still be able to use google for research, no?

Again, I'd prefer not to have to forbid stuff entirely as I have more tools at my disposal as a parent.

---

### Post by scrupul0us on 2007-02-09
well... use a hosts file to just block all the garbage to begin with... myspace is a waste of time IMHO anyways so just block it

127.0.0.1 myspace.com
127.0.0.1 login.myspace.com

---

### Post by kpatz on 2007-02-09
Your daughter does her homework on a Linux box? ;)  Or is she on a Windows box that is connected to the internet via a Linux box?

If it's the latter (or the former even), you can restrict access via iptables (firestarter) or Squid.  You could use cron jobs to set times to allow or restrict access.

---

### Post by scrupul0us on 2007-02-09
if you are really concerned just setup rules for her MAC address on your router and be done with it... thats by far the easiest solution if u have a decent router (linksys)

---

### Post by haochela on 2007-02-14
I liked the first idea the best, actually, because shutting down access through a cron script actually gives me more flexibility in allowing my daughter access at set times to certain programs without making it an "all or nothing" approach for all of time. If she can operate and succeed within her limitations then she we can look at allowing her more freedom. We get her to study and she gets to see the light of day.

The only problem is, this script doesn't seem to work as a cron job. I tested the command out as root and found it shuts down root but not the ordinary user.I can still run gaim as an ordinary users and the cron daemon doesn't seem to execute the scrip the way it's supposed to (I used gcron to set it up).  Is it possible thes commands  don't set the permissions the way we need to set them to shut down access? Also, what is the process I'm supposed to follow on the command line to update the cron job so that it reads it right away.

Any suggestions would be very helpful.

---

### Post by haochela on 2007-02-14
Also could you provide an example of ways to restrict myspace using iptables. In answer to your question, I've got her on a little pavillion with Dapper Drake loaded.

---

### Post by gaten on 2007-02-14
Use this script to restrict executable permission for gaim. In order for these to work, gaim HAS to be closed already. You could ensure this thus:
```
#!/bin/bash
killall gaim
chmod 744 /usr/bin/gaim

```

That kills any running gaim clients and removes executable permission with octal codes. 
I tested this on my dapper system just to make sure, and it works fine. She'll get a nice little 'Permission Denied' pop up when she tries to run it. That is of course assuming gaim is in /usr/bin/gaim (mine is), you can find out for sure with 
```
which gaim
```

Use this script to enable executable permission again:
```
#!/bin/bash
chmod 755 /usr/bin/gaim
#/usr/bin/gaim &
```

That will enable execution of the gaim client again and run it in the background if you so choose (you have to remove the # from the begging of the '#/usr/bin/gaim &' line first). This way, she'll know it's "play time" again. Hope this helps

NOTE: A more dynamic script might be:
```
#!/bin/bash
killall gaim
chmod 744 `which gaim`

```

Note that the ` are the ones next to the number 1 (the ~ key). But that seems really redundant to me, as you can simply find out where gaim is and then put that path into the script. Please be aware that if she can run anything as root (sudo) that won't work if she's smart. She can simply chmod 755 it herself or even just run it as root and bypass all that.

Sorry, can't help you with your iptables script, not my thing. Good Luck.

---

### Post by haochela on 2007-02-15
OK,
 I written two scripts called startgaim.sh and stopgaim.sh that are set up as executable files and are each referenced in  a crontab that is located in my home directory. I have this crontab file  set as my default crontab file but it doesn't execute. Why? What are the steps I need to perform in order for the job to kick off properly?

This is the output from my user's crontab file:

05 18 * * Mon-Fri /home/[my-directory]/stopgaim.sh
30 20 * * Mon-Fri /home/[my-directory]/startgaim.sh

---

### Post by gaten on 2007-02-16
Not sure why it doesnt work. Just try adding those lines to /etc/crontab (after you make a backup) rather than the one in your home dir.

---

### Post by lenwood on 2007-02-18
FWIW, if you want to restrict instant messaging, then you may also consider blocking access to Meebo.com. That site allows you to log into any chat client via the web (check it out for yourself, its pretty slick, really). Its becoming more prevalent on college campuses, so its only a matter of time before your daughter realizes that gaim isn't required for chatting.

HTH,
Thanks,
Len

---

### Post by haochela on 2007-02-19
Thanks for the advice. Editing chrontab.etc and running the chmod command as root fixed the issue. Too bad I couldn't get it to work running from my account. Perhaps the use of cron is limited in the user space?

Thanks for the heads up on meebo.com.

---

### Post by haochela on 2007-02-19
Thanks for the advice. Editing chrontab.etc and running the chmod command as root fixed the issue. Too bad I couldn't get it to work running from my account. Perhaps the use of cron is limited in the user space?

Thanks for the heads up on meebo.com.:)

---

### Post by madcap_magician on 2007-02-19
> **haochela said:**
> OK,
 I written two scripts called startgaim.sh and stopgaim.sh that are set up as executable files and are each referenced in  a crontab that is located in my home directory. I have this crontab file  set as my default crontab file but it doesn't execute. Why? What are the steps I need to perform in order for the job to kick off properly?

This is the output from my user's crontab file:

05 18 * * Mon-Fri /home/[my-directory]/stopgaim.sh
30 20 * * Mon-Fri /home/[my-directory]/startgaim.sh


I've had similiar problems, I can't get cron to run any file that has an extension on it.  Try renaming the files without the .sh extension and removing the extensions on crontab.

---

### Post by nigelenki on 2007-02-19
MySpace is a problem because 16 is the age of consent here and every guy I know who has an account uses it for the sole purpose of getting 16 year old high school girls over for sex.  (Can you tell I hate MySpace?)

Other than that, Internet + instant message can be useful resources; I use those and IRC to gather information all the time.  Spent some time in #math to get some help on Calc 2 the other day :)

---

### Post by haochela on 2007-02-20
Those are all good points. I put myspace and meebo into hosts deny. Myspace is definitely a problem, but I have a year or two (I hope!) before I have to worry about the "age of consent". Besides, I'd just as soon see how she manages her time and relationships first before I go full bore into forbidding everything all the time.

Which reminds me. Is there any way, after say, the third attempt, I can get a pop-up to come up that says: GET BACK TO WORK OR YOUR MOTHER AND I WON'T TAKE YOU TO GYMNASTICS!

---

### Post by haochela on 2007-02-27
> **scrupul0us said:**
> well... use a hosts file to just block all the garbage to begin with... myspace is a waste of time IMHO anyways so just block it

127.0.0.1 myspace.com
127.0.0.1 login.myspace.com

I tried adding this in /etc/hosts.deny, but it failed to block myspace. Is there another file I'm supposed to be using or a service I have to restart after changing it?

---

### Post by gaten on 2007-03-01
Quote:
 	 	 		 			 				 					Originally Posted by **scrupul0us** 					[[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://www.ubuntuforums.org/showthread.php?p=2128502#post2128502") 				
 				[I]well... use a hosts file to just block all the garbage to begin with... myspace is a waste of time IMHO anyways so just block it

127.0.0.1 myspace.com
127.0.0.1 login.myspace.com[/I]
 			 		 	 	 
I tried adding this in /etc/hosts.deny, but it failed to block myspace. Is there another file I'm supposed to be using or a service I have to restart after changing it?

Not hosts.deny, but /etc/hosts. hosts.deny tells your machine which hosts to deny access from, and that only works if the service you are using is compiled with TCP_WRAPPERS support. 

Put the above entry into /etc/hosts, that will tell your computer to resolve myspace.com and login.myspace.com into your local machine.

---

### Post by scxtt on 2007-03-01
> **haochela said:**
> OK,
 I written two scripts called startgaim.sh and stopgaim.sh that are set up as executable files and are each referenced in  a crontab that is located in my home directory. I have this crontab file  set as my default crontab file but it doesn't execute. Why? What are the steps I need to perform in order for the job to kick off properly?

This is the output from my user's crontab file:

05 18 * * Mon-Fri /home/[my-directory]/stopgaim.sh
30 20 * * Mon-Fri /home/[my-directory]/startgaim.sh

that's the wrong format for a cron job ... there is no "Mon-Fri" ,,, try doing this instead:

**ps -ef | grep cron** #to make sure a cron daemon is running (if it isn't, **sudo /etc/init.d/cron start** should take care of it)
**crontab -e** #to edit your crontab, will also do syntax checking on close

add entries of this form:
```
[font=courier]30 8    * * 1,4 scxtt   mailx -s "bashrc" user@email.com < /home/scxtt/.bashrc[/font]
```
this will run my "mailx" command (as me) @ 8:30am on the 1st and 4th days of the week ...

i generally add entries to /etc/crontab as root in that form, so you may find that you don't need to use the username (scxtt in my example) when doing **crontab -e** ... let me know if you have any probs ...

---

