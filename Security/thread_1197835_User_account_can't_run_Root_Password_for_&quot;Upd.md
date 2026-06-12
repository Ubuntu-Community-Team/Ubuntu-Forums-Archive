---
title: "User account can't run Root Password for &quot;Update Manager&quot; or in sudo"
date: 2009-06-26
forum: Security
---

### Post by Ed Lagniappe on 2009-06-26
I'm wearing a hole in the wall ... & rubbing off my hair ... banging my head against the wall on this one.

Obviously, I'm a newbie w/ Ubuntu ... but I learned on CP/m & DOS 2.1 ... so the Terminal isn't a big problem for me.

But, using good security advice, I am trying NOT to use the Root Acct online.  But everytime I get into the User account & run "Update Manager" it prompts me for the admin password ... if I put in the root password, it tells me I've entered the wrong password.  If I put in the User password ... same deal.

I KNOW I'm entering the root password correctly ... I can't have entered it wrong 50 times in the User acct but always get it right when I sign onto Root.

I'm having similar problems doing sudo in terminal from the User account.

Obviously, I've overlooked something simple, but I'm not finding the answer in any of the docs or instructions for idjit beginners.

Being an idjit beginner, I'm accumulating a set of instructions to get friends started on Ubuntu ... but if it won't work for me, I won't be able to sell them.

Thanks for help w/ this password problem.

Ed

---

### Post by Agent ME on 2009-06-26
What do you mean by root password? There shouldn't even be a password set for root.

When you use your use account and use sudo, you enter the user's own login password. If this doesn't work, make sure you're in the admin group. Just type "groups" in a terminal to see what groups your account is part of.

---

### Post by Divider on 2009-06-26
In jaunty when you do a:
```
sudo apt-get update
```

Your update manager already loads with root permission from the previous command. so if you just login with a regular account (with sudo privlages) you can update your system without the fear of exposing a root password. 

But as Agent ME stated above, you should not need to enter a root password because one is not set by default in ubuntu.

Also as a side note, loggin into root directly is a major security issue, it means anything you click on, a link, a program, a script, ANYTHING; has instant permission to do as it pleases.

---

### Post by bodhi.zazen on 2009-06-26
This page should help :

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by jimasbille on 2009-09-10
I've been using Linux for Nine years but just setup my first Ubuntu multi-user box.  I have had a box with 5 users in OpenSuse for years but I have been baffled by the Ubuntu password thing since I installed two days ago.

For each user, when they need administrative access do they enter *their* password?  In Suse they entered the root password so I have tried using the first users password thinking that was "root".

---

### Post by cariboo on 2009-09-10
If a user has sudo privileges, they have to enter their own password for any functions that need root privileges.

---

### Post by Eagles42 on 2009-09-16
hello i have install ubuntu few days ago i was exited and i start download software i also download edubuntu than i restart my pc and than i saw the screen of edubuntu and not ubuntu i try to login i was forgotten my username & password i try now for more  than tree days to login nothing helps i have the cd of ubuntu i hope someone
can help me 
 
Eagles42

---

### Post by jimasbille on 2009-09-16
> **jimasbille said:**
> I've been using Linux for Nine years but just setup my first Ubuntu multi-user box.  I have had a box with 5 users in OpenSuse for years but I have been baffled by the Ubuntu password thing since I installed two days ago.

For each user, when they need administrative access do they enter *their* password?  In Suse they entered the root password so I have tried using the first users password thinking that was "root".

All is good, I added all users to Sudo and they user their own passwords.

---

### Post by cariboo on 2009-09-16
If you don't remember your user name and password, start in in recovery mode. Press esc when you see the grub menu and use the arrow keys to navigate to recovery mode, then press enter. You will see Ubuntu loading and eventuality it will come to a menu, use the arrow keys to select drop to root prompt. Once at the prompt type:

```
ls -l /home
```

you should see your home directory listed by your user name eg:

```
ls -l /home
total 20
drwxr-xr-x 15 jim jim  4096 2009-09-16 12:52 jim
drwx------  2 root root 16384 2009-09-16 09:40 lost+found
```

My home directory is called jim. Once you have found your user name at the prompt type:

```
passwd <username>
```

where <username> is your user name. Enter a password, it will not be echoed back, then enter it again. 

Once you have created a new password type exit, then select resume from the menu. This will take you to your desktop.

---

### Post by Triksiklist on 2010-01-22
Can someone please help?
I lost my password so I tried to follow the instructions re: Grubmode, whatever that is? Got to "Drop to Root Prompt". tried typing ls-l/home but just got "no such command!
All this strange language completely baffles me I'm afraid.
I am getting fed up with Ubuntu, it wont give me the BBC website, it won't run my T-Mobile Mobile Dongle, the Curser dissapears when trying to send e-mails, I cannot download Flash Player, it all seems extremely complex just to use basic operations!
Can someone releive my misery please?
Ken:(

---

### Post by sisco311 on 2010-01-22
> **Triksiklist said:**
> Can someone please help?
I lost my password so I tried to follow the instructions re: Grubmode, whatever that is? Got to "Drop to Root Prompt". tried typing ls-l/home but just got "no such command!

This should help:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Check out the other tutorials on the site as well.
i.e. [http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash) ;)
&
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

btw, the command is:
```
ls -l /home
```

---

