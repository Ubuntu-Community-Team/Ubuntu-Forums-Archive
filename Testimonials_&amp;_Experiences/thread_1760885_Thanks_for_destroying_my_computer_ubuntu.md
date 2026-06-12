---
title: "Thanks for destroying my computer ubuntu"
date: 2011-05-17
forum: Testimonials &amp; Experiences
---

### Post by TheCompBoy on 2011-05-17
Hello thank you for destroying my computer with your new version you idiots making ubuntu you totaly ruined your operative system with the new version.. Also you ruined my computer which i now have to send to repair.. 
I realy hope you close this project becasue you are no longer making it seriously.
Also i think you can get out of the programming buisness cause i found out you don't use ur heads to something usefull like upgrading your system making it better, You use your knowledge to destroy whole thing.. That realy show's how "Intelligent"you realy are.

Okay i finished my quick message. 

P.S This post may be very vulgar but its only cus i am realy angry about this.

---

### Post by TeoBigusGeekus on 2011-05-17
> **TheCompBoy said:**
> Hello thank you for destroying my computer with your new version you idiots making ubuntu you totaly ruined your operative system with the new version.. Also you ruined my computer which i now have to send to repair.. 
I realy hope you close this project becasue you are no longer making it seriously.
Also i think you can get out of the programming buisness cause i found out you don't use ur heads to something usefull like upgrading your system making it better, You use your knowledge to destroy whole thing.. That realy show's how "Intelligent"you realy are.

Okay i finished my quick message. 

Hope you burn in hell Ubuntu Team.

An operating system can't ruin your hardware...
What happened? Please tell us.

---

### Post by TheCompBoy on 2011-05-17
I upgraded to new version of ubuntu and the when restart all the bars was gone... I can't open anything i can't close anything.. What is this..

Wait im going to post a picture

---

### Post by TeoBigusGeekus on 2011-05-17
You probably mean the panels.
When you log in, you can choose the "Ubuntu Classic" session - this would probably bring your panels back.
Even so, having lost your panels is not actually a destruction of your pc.
We could work it out, if you're interested that is.

---

### Post by syscreat on 2011-05-17
> **TheCompBoy said:**
> Hello thank you for destroying my computer with your new version you idiots making ubuntu you totaly ruined your operative system with the new version.. Also you ruined my computer which i now have to send to repair.. 
I realy hope you close this project becasue you are no longer making it seriously.
Also i think you can get out of the programming buisness cause i found out you don't use ur heads to something usefull like upgrading your system making it better, You use your knowledge to destroy whole thing.. That realy show's how "Intelligent"you realy are.

Okay i finished my quick message. 

P.S This post may be very vulgar but its only cus i am realy angry about this.

Ubuntu team creat Unity, it's not useful for every users. And no choose in installation process. It's bad idea. -- It's only my opinion.

---

### Post by oaxacamatt1 on 2011-05-17
Hey Compboy,
I have to empathize but also agree with Teo, Ubuntu by itself will not trash your computer.  I have to imagine it was something else, such as the age of the hardware, etc.  If you want help you could give more details but if you want to be talked 'off that ledge' you are on then...

---

### Post by TheCompBoy on 2011-05-17
The red i marked is what not exist in my ubuntu... Nothing there..

Yes may be panels.. But thing is after this i can't re-install any operative system.. I can't do nothing.

---

### Post by TeoBigusGeekus on 2011-05-17
Do you have Automatic Login enabled?
If not, you can choose "Ubuntu Classic" when you log in.

---

### Post by uRock on 2011-05-17
Not a support request. Moved to Testimonials.

---

### Post by TheCompBoy on 2011-05-17
Yes i have automatic login..

---

### Post by StrayEddy on 2011-05-17
At boot up, change the interface for classic desktop, you should be fine then.

---

### Post by TeoBigusGeekus on 2011-05-17
Ok, press Ctrl+Alt+T.
This should bring up the terminal.
If it does, give
```
gnome-session-save --kill
```
It should log you out (at least it used to when the desktop was gnome).
If you manage to log out, choose "Ubuntu Classic" from the sessions menu (down rightish) and log back in.

---

### Post by TheCompBoy on 2011-05-17
I have automatic login.. I can't make this.. I told please read before posting.

---

### Post by kaldor on 2011-05-17
Yes, send the computer for repair because of a minor bug.

:)

---

### Post by TheCompBoy on 2011-05-17
Okay Theo i will try this give me 2 min

---

### Post by StrayEddy on 2011-05-17
> **TeoBigusGeekus said:**
> Ok, press Ctrl+Alt+T.
This should bring up the terminal.
If it does, give
```
gnome-session-save --kill
```
It should log you out (at least it used to when the desktop was gnome).
If you manage to log out, choose "Ubuntu Classic" from the sessions menu (down rightish) and log back in.
 
 
OR Ctrl-Alt-F1

---

### Post by TheCompBoy on 2011-05-17
> **kaldor said:**
> Yes, send the computer for repair because of a minor bug.

:)
Call it whatever you whant.. i don't care about your opinnion

---

### Post by TheCompBoy on 2011-05-17
> **TeoBigusGeekus said:**
> Ok, press Ctrl+Alt+T.
This should bring up the terminal.
If it does, give
```
gnome-session-save --kill
```It should log you out (at least it used to when the desktop was gnome).
If you manage to log out, choose "Ubuntu Classic" from the sessions menu (down rightish) and log back in.
I tryed not.. I set to "Ubuntu Classic" and i login.. Nothing happends.

---

### Post by potat on 2011-05-17
> **TheCompBoy said:**
> Yes i have automatic login..

Try this:

1. Hit ctrl-alt-f1 to enter a virtual terminal and log in with your username 
2. Type the command ```
sudo nano /etc/gdm/custom.conf
``` and enter your password again 
3. In this file, change ```
automaticloginenable=true
``` to false 
4. Hit ctrl+x, y, then enter to save and quit 
5. Enter ```
sudo reboot
```

You should get a login window at boot now, probably with an auto-login countdown, so make sure you catch it in time to switch your session to Ubuntu Classic.

I stole this from [http://askubuntu.com/questions/40133/unity-not-showing-after-11-04-upgrade-cannot-log-out-to-switch-to-classic](http://askubuntu.com/questions/40133/unity-not-showing-after-11-04-upgrade-cannot-log-out-to-switch-to-classic)

Hope this helps.

---

### Post by StrayEddy on 2011-05-17
If you type in the terminal:
 
"gdm"
or
"startx"
 
what does it say?

---

### Post by wojox on 2011-05-17
Try 

```
gksudo gdmsetup
```

---

### Post by TheCompBoy on 2011-05-17
> **potat said:**
> Try this:

1. Hit ctrl-alt-f1 to enter a virtual terminal and log in with your username 
2. Type the command ```
sudo nano /etc/gdm/custom.conf
``` and enter your password again 
3. In this file, change ```
automaticloginenable=true
``` to false 
4. Hit ctrl+x, y, then enter to save and quit 
5. Enter ```
sudo reboot
```You should get a login window at boot now, probably with an auto-login countdown, so make sure you catch it in time to switch your session to Ubuntu Classic.

I stole this from [http://askubuntu.com/questions/40133/unity-not-showing-after-11-04-upgrade-cannot-log-out-to-switch-to-classic](http://askubuntu.com/questions/40133/unity-not-showing-after-11-04-upgrade-cannot-log-out-to-switch-to-classic)

Hope this helps.

I already got so far so i had the option to set to Ubuntu Classic but when i login its still same..

---

### Post by drs305 on 2011-05-17
Another possible option if you are actually running Natty's Unity:
Press the 'Windows' button or ALT-F2. If that opens a window, type "System Settings" and click on the System Settings icon.

Then go to the System section, Login Screen. From there you can change the automatic login and also elect to log on with Ubuntu Classic.

---

### Post by TheCompBoy on 2011-05-17
> **drs305 said:**
> Another possible option if you are actually running Natty's Unity:
Press the 'Windows' button or ALT-F2. If that opens a window, type "System Settings" and click on the System Settings icon.

Then go to the System section, Login Screen. From there you can change the automatic login and also elect to log on with Ubuntu Classic.
Am on it give me a minute.

---

### Post by TeoBigusGeekus on 2011-05-17
My guess is that some settings from your old ubuntu installation conflict with the new, natty settings.
As a first plan, you could try adding a new user in your system, to see if a new, fresh, user account works ok.
If you can reach a terminal, give
```
sudo adduser
```
Follow the instructions and answer all the questions.
Next, add a password for this user
```
sudo passwd NewUserName
```
Replace NewUserName with the user name you gave while executing the adduser command.
Give your new password and then
```
sudo reboot
```
to... reboot (surprise!!!).
The next time you log in, choose the new user and see if every(any)thing works.

---

### Post by TheCompBoy on 2011-05-17
> **TeoBigusGeekus said:**
> My guess is that some settings from your old ubuntu installation conflict with the new, natty settings.
As a first plan, you could try adding a new user in your system, to see if a new, fresh, user account works ok.
If you can reach a terminal, give
```
sudo adduser
```Follow the instructions and answer all the questions.
Next, add a password for this user
```
sudo passwd NewUserName
```Replace NewUserName with the user name you gave while executing the adduser command.
Give your new password and then
```
sudo reboot
```to... reboot (surprise!!!).
The next time you log in, choose the new user and see if every(any)thing works.
Give me a second.. I realy whana fix this so i can get back to programing.
If it gets fixed i actualy can say sorry to ubuntu team.

---

### Post by TheCompBoy on 2011-05-17
Thanks TeoBigusGeekus for your realy good help!

Thanks to you i can now run my ubuntu computer atleast...

I whant to say sorry to Ubuntu Team hope you accept my excuse and hope its cool between us.. 

Peace out people!

---

### Post by TeoBigusGeekus on 2011-05-17
Wait, we have a bit more work to do.
You don't have to lose everything from your old account.
In the Places menu, you can find your old home folder and copy and paste your favourite programs' configuration files to your new account.
If, for example, you use Opera as I do, you can copy your old .opera folder from your old /home to your new one: this way, when you open opera in your new account, you will see all your bookmarks and settings intact.
Do the same for every other app that you care about.

After you're done, do a 
```
sudo userdel -r your_old_user_name
```
This command will delete both your old account, as well as your old home folder.

PS: Never do an upgrade with Ubuntu; I've never done one that worked. Always go for a clean installation.

---

### Post by TheCompBoy on 2011-05-17
Thanks man more the better!

---

### Post by TeoBigusGeekus on 2011-05-17
Welcome back and don't forget to mark the thread as solved.

---

### Post by aphatak on 2011-05-17
Proves my point - again - that the Ubuntu forums and the community is the biggest value Ubuntu has for me - and, I suspect, for a large number of Ubuntu users.

The community has people who (a) know what they are talking about, (b) have the genuine desire to solve the problem, (c) stick around until the problem is actually resolved, and (d) go above and beyond the call of duty to offer advice and help afterwards.  And the forum finds at least one such person within minutes - as I counted it, it took 54 minutes to turn a seriously irritated user who was ready to don sack-cloth-and-ashes into someone who has re-joined the community as a happy and productive member.

I can imagine what would have happened if the OS in question was of the commercial, paid-for variety:  the irate user would have been talking to someone in a call-center on the other side of the world, and that someone would have no more knowledge than what a rudimentary training and a pre-written script would provide.  I am willing to bet the problem would not have been solved this quickly.

---

### Post by 3 frags left on 2011-05-17
Lol, I thought this was a troll thread, but... oh, nevermind. Close it?

---

### Post by el_koraco on 2011-05-17
> **TeoBigusGeekus said:**
> Wait, we have a bit more work to do.
You don't have to lose everything from your old account.
In the Places menu, you can find your old home folder and copy and paste your favourite programs' configuration files to your new account.
If, for example, you use Opera as I do, you can copy your old .opera folder from your old /home to your new one: this way, when you open opera in your new account, you will see all your bookmarks and settings intact.
Do the same for every other app that you care about.

After you're done, do a 
```
sudo userdel -r your_old_user_name
```
This command will delete both your old account, as well as your old home folder.

PS: Never do an upgrade with Ubuntu; I've never done one that worked. Always go for a clean installation.

Whoa, don't you think he should add himself to the sudoer group? 

Compboy, are you running the "Ubuntu" or the "Ubuntu classic" session?

---

### Post by TeoBigusGeekus on 2011-05-17
> **el_koraco said:**
> Whoa, don't you think he should add himself to the sudoer group? 

Forgot about that...
He can do it later I guess.

---

### Post by IWantFroyo on 2011-05-17
Sounds like an edd=on issue.
Reboot and hold esc after your manufacturer's screen until you get the GRUB menu, press 'e' on the first option, and just add edd=on at the end. It will make Ubuntu read your discs in a slightly different way, and will probably fix Unity.

---

### Post by el_koraco on 2011-05-17
> **TeoBigusGeekus said:**
> Forgot about that...
He can do it later I guess.

Well, it's gonna be hard if he deletes the only user account with sudo privileges. In your dark Arch days you forgot that Ubuntu has no root account enabled by default. 
I guess we'll be hearing from him later, and some more cli voodoo's gonna be needed :D

---

### Post by TeoBigusGeekus on 2011-05-17
Meh... no big deal. He can edit the sudoers file with a live cd using nano.
Visudo is recommended, not necessary to edit the file.

---

### Post by arunb on 2011-05-18
so where did the OP send the computer to be repaired ??
Are there any linux technicians who do such repair jobs ??

---

### Post by TAspr on 2011-05-18
You guys are incredible!  Thank you for making this forum a productive part of the whole Linux society.  This is fantastic that you guys are willing to help a guy in crises and come to the rescue.  Way to go!

---

### Post by uRock on 2011-05-18
> **arunb said:**
> so where did the OP send the computer to be repaired ??
Are there any linux technicians who do such repair jobs ??

There's a shop about a mile away where they advertise Linux service. I have only entered once, because they sell used laptops and such and I was hoping to get a deal. Their prices discouraged me from wanting to return.

---

### Post by rewyllys on 2011-05-18
> **arunb said:**
> so where did the OP send the computer to be repaired ??
Are there any linux technicians who do such repair jobs ??
To find local people who could help you, I'd suggest that you look at your local Craigslist.  Try searching the term "linux" in "Computer Services" (or something close to that).

---

### Post by TheCompBoy on 2011-09-13
Damn.. I had now some time to think over what i said in this forum and what i did.. I'm very happy that i got this much help and all.. And i want to say sorry for all the mean things i said.. Next time i will investigate and maybe try to learn something.. Again am very sorry.

---

### Post by XubuRoxMySox on 2011-09-13
> **TheCompBoy said:**
> Damn.. I had now some time to think over what i said in this forum and what i did.. I'm very happy that i got this much help and all.. And i want to say sorry for all the mean things i said.. Next time i will investigate and maybe try to learn something.. Again am very sorry.

A lesser person would not have bothered with an apology! It's like the saying, "one who is forgiven much, loves much!"

Because of your experience, you may turn out to be a great asset to this community and the awesome distro it is built around.

Best of hopes and encouragement to you!

---

### Post by Arthur_D on 2011-09-13
Yeah, nice going man. :)

---

### Post by Elfy on 2011-09-14
Closed - old testimonial.

---

