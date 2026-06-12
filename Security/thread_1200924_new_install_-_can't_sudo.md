---
title: "new install - can't sudo"
date: 2009-06-30
forum: Security
---

### Post by awerking on 2009-06-30
Hi all from a noob.  Have been using Uduntu 9.04 on an old desktop for a couple weeks now, and have learned a lot - I'm liking Ubuntu!  Just completed an Xubuntu install on an old Inspiron 2500 laptop and I've run into an issue that I can't work around.

When I try to run a sudo command I get a warning that says that I am not and authorized "sudoer".  Also, I am locked out of all of the system admin settings.  When I try to log in as root from the main screen it tells me that root cannot login from there.

Where do I need to login in from as root to give my main user account sudo and admin priviliges?

Thanks!

---

### Post by sisco311 on 2009-06-30
By default, the root account password is locked. If you have enabled the root account, then switch to a virtual terminal(Ctrl+Alt+F1), log in as root and add your user to the admin group:
```
adduser username admin
```

If not, then:
[http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by Polaris96 on 2009-06-30
careful, partsdale ... they come in the night ... lol

---

### Post by awerking on 2009-06-30
Thanks, Sisco.

I did enable the root account when I installed, and I can access the root account if I hit escape at boot, go into the alternative boot mode, and login to root on the command line.   I couldn't figure out how to add my main user account to the admin group.  

This should do the trick - I'll give it a try.  Thanks!

Polaris - This is a brand new install on an OLD laptop - had to use the alt install cd and could only complete the install by using apci off and expert modes.  I'm guessing I failed to properly execute the step during the text based configuration that would have added my main user account to the admin group.  Lesson learned...

---

### Post by Polaris96 on 2009-06-30
I'm just glad you're up and running :)  

nice one, sisco.  

awerkin, I'm glad you learned how to use root and I disagree with ubuntu's philosophy of denying the knowledge to a user.  That said, don't talk too much about it here - they get mad .... omg!  I think they're coming!  ohshit - no - NO AGAGAGGAGAGAGGAGGGGGGGHHHHHHHHH!  ;P

---

### Post by cariboo on 2009-06-30
Running as root is not part of Ubuntu's take on security. There are more mistakes made because people forget they are running as root, so in order to keep new users from accidently making their installation unusable, the root account has been disabled. 

My personal view is that if you have to ask on the forum how to enable root, you aren't ready to do it.

---

### Post by ronaldprettyman on 2009-06-30
**Step 1 **Reboot the machine (note your want to print/write this down)
**Step 2**After the system post the initial memory test oem logo screen keep hitting the esc key
**Step 3**Your get a menu
See some options
This is grub..more then likely could be lilo but I doubt it
**Step 4**Select the second option for restore mode
```
Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)

```
It will boot into single user mode
**Step 5**Your be given a Blue Screen, select exit to prompt, or goto prompt or shell, I don't know the exact wording off the top of my head but something along those lines.

Now once your at the shell use your favorite editor to execute these commands
if its vi or emacs just replace nano with that, I recommend nano, cause you've already said your a noob

Now your want to know your username, exactly as its spell case senstative, just run this and look at the last couple of lines to see the exact spelling of your username
**Step 6**```
cat /etc/passwd
```
Your see something like this
```
ron:x:1000:1000:ron,,,:/home/ron:/bin/bash
sshd:x:112:65534::/var/run/sshd:/usr/sbin/nologin
random1:x:1001:1001:,,,:/home/random1:/bin/bash
mysql:x:113:125:MySQL Server,,,:/var/lib/mysql:/bin/false
statd:x:114:65534::/var/lib/nfs:/bin/false
```
where ron in this case is my default/main username.
So now take that and put it into your suduers file
**Step 7**```
nano /etc/sudoers
```
look for a line that looks exactly like this
```
root    ALL=(ALL) ALL
```
just underneath it add
```
ron     ALL=(ALL) ALL
```
where ron would be your default main username
now your should be good to go
**Step 8**to check this reboot your system, log in as your default username
**Step 9**and open a terminal (alt+f2) xterm
enter the following
**Step 10**```
sudo whoami
```
with the correct response being
```
root
```
if for some reason you have it set to auto login and you can't sudo because you forgot your password
repeat steps 1-5
when you get to a prompt type
```
passwd ron
```
where ron is your default/main username
enter a new password, write it down, remember it
then repeat steps 8-10, you should be successful now

---

### Post by awerking on 2009-07-01
SUCCESS!!  Thanks, Sisco and Polaris!

Looks like I botched something on my install from the alt. cd because my system didn't have a user listed in the admin group.  Consequently, my sudo file was whacked.  I ended up having to add myself to the admin group from root, and then I had to rewrite the sudo file per the phychocats link listed in Sisco's earlier post.

Ronald - Thanks for taking the time to give me an alternative method.  Turns out my sudo file needed a little more tidying up.  The steps listed in the psychocats link did the trick for me.

Thanks to everyone for the help!

---

