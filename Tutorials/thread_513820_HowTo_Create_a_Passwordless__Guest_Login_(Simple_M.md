---
title: "HowTo: Create a Passwordless / Guest Login (Simple Method)"
date: 2007-07-30
forum: Tutorials
---

### Post by aysiu on 2007-07-30
Yes, I realize such a HowTo already exists ([HowTo: enable passwordless logins via GDM](http://ubuntuforums.org/showthread.php?t=123116)), but this method is entirely different and, I think, less complicated.

**Warning**: Even though this method is simple (few steps), it is *extremely* dangerous if you don't know what you're doing. Do not attempt this if you are worried that you might mess up the /etc/shadow file, thus screwing up your Ubuntu system, possibly irreparably!

This is an oft-requested task, mainly for people who don't want to require less tech-savvy family members to have to remember passwords. It is a security risk, but I think people should at least *know* how to put their computers at risk if they want to. Don't blame me if anything bad happens.

**Step 1**
Make sure you have created a user. For the sake of this example, let's say you called the account username *guest*. You can give it any temporary password you want. We're going to change that password shortly anyway. I'm assuming you know how to do this already. If you don't, I can assure you that this HowTo is not one you should be following, and you would be very likely to screw up the next step. 

**Step 2**
Next, go to [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste in this command: ```
sudo nano -B /etc/shadow
``` This will open the /etc/shadow file (the one that contains all the passwords) in a text editor called Nano.

Once you have it open, find the appropriate line for the account in question. It'll look something like this: ```
guest:**$1$2TUdk8Z0$tb2Fn6Idgo8dq9EgYv4xZ0**:13721:0:99999:7:::
``` Change the second part (in bold here) to match this second part (also in bold): ```
guest:**U6aMy0wojraho**:13721:0:99999:7:::
``` Then save the file (Control-X, Y, Enter).

Now you should be able to log into the *guest* (or whatever you called it) account without entering a password.

---

### Post by wieman01 on 2007-07-31
Nice one, Aysiu!

---

### Post by aimran on 2007-07-31
Would this give the guest sudo access at the terminal?

---

### Post by wieman01 on 2007-07-31
> **aimran said:**
> Would this give the guest sudo access at the terminal?
If you give the guest account administrative rights, yes. Otherwise it shouldn't.

---

### Post by Frak on 2007-07-31
Great job Aysiu! Very helpful.

---

### Post by aysiu on 2007-07-31
> **aimran said:**
> Would this give the guest sudo access at the terminal?
No. This has *nothing* to do with user privilege. It has only to do with the user password being blank.

If you want to add your guest user to the *admin* group, then that's a separate step, and one I would **strongly** advise against.

---

### Post by andrewsomething on 2007-07-31
@Aysiu

Worked like a charm. Would you mind explaining a little more? I assume "U6aMy0wojraho" is the encryption for nothing?

---

### Post by aysiu on 2007-07-31
> **andrewsomething said:**
> @Aysiu

Worked like a charm. Would you mind explaining a little more? I assume "U6aMy0wojraho" is the encryption for nothing?
I would assume the same thing. More details on how I figured this out:
[http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/](http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/)

---

### Post by Frak on 2007-08-01
Didn't think about looking at that, aysiu. Good thinking :)
Pretty clever.

---

### Post by andrewsomething on 2007-08-01
@Aysiu

> So I looked at the /etc/shadow file, which holds encrypted passwords for all users, on the live CD and found that the encrypted password for the user ubuntu is U6aMy0wojraho. So I tried editing the /etc/shadow file on my own installation of Ubuntu and changing the password for a test user from its previous encrypted password to U6aMy0wojraho, and I was able to log in as that user without entering a password.

Cool! 

Thanks for mucking around your with system to figure that out....

---

### Post by timmie on 2007-08-09
Hello,
I am really wondering why it is that dificult to have a gues account.

I asked again on Launchpad:
[https://answers.launchpad.net/ubuntu/+question/8897](https://answers.launchpad.net/ubuntu/+question/8897)

My requirements are as follows:

[LIST]
[*]needs no password: I type in the user name "Guest" and get staright to the desktop
[*] is locked down to only access the home directory of guest. No other drives such as additional fat32 data partitions etc.
[*] configuration files like firefox and gaim get cleaned after log out.
[/LIST]

If I lock down the data access of that account it would not be too difficult to maintain security.

What do you think?
Any ideas?

---

### Post by aysiu on 2007-08-09
I think you're looking for something *beyond* a passwordless login. You're looking for a kiosk mode:

[Lock down the GNOME desktop with Pessulus](http://www.linux.com/feature/62060)
[Kiosk Admin Tool](http://extragear.kde.org/apps/kiosktool/)

---

### Post by oiler920 on 2007-08-12
Thank you aysiu soooooo much! :guitar:

---

### Post by balance07 on 2007-09-03
I have a problem with this method:

i can login fine w/ no password to my "guest" account, but can't get BACK into it after switching user to a normal account, then trying to get back to the guest account. can't unlock the guest account screen. any tips?

---

### Post by nightfrost on 2007-09-30
Thanks a lot for this workaround. I've been really trying to find a fix for this problem and I really can't understand why this feature isn't implemented yet. I mean, it can't really be for security reasons since the option would be, well an *option* and hence it could be turned off. Well, I'm not going into that. Just writing to say thanks.

But I can't help wondering: What makes it work? I'd guess the string is an encrypted version of <ENTER>. But I wouldn't know...

---

### Post by Frak on 2007-09-30
> **nightfrost said:**
> Thanks a lot for this workaround. I've been really trying to find a fix for this problem and I really can't understand why this feature isn't implemented yet. I mean, it can't really be for security reasons since the option would be, well an *option* and hence it could be turned off. Well, I'm not going into that. Just writing to say thanks.

But I can't help wondering: What makes it work? I'd guess the string is an encrypted version of <ENTER>. But I wouldn't know...
Actually, its an encrypted version of nothing.

---

### Post by wieman01 on 2007-10-01
> **Frak said:**
> Actually, its an encrypted version of nothing.
Haha... :-) You made my day, Frak.

---

### Post by Frak on 2007-10-01
> **wieman01 said:**
> Haha... :-) You made my day, Frak.
:)

---

### Post by Niniel on 2007-10-08
Btw, I recently got hold of a computer with Fedora 8 on it, and that lets you set a blank password with the click of the mouse. It also uses the Gnome desktop so I was very surprised to find that Ubuntu doesn't have that feature.
Correction, on second thought, I think it just allows you to let a user log in without password, which I think is not quite the same as having no password.

---

### Post by Duwady on 2007-10-08
I have installed a samba server for keeping files and for print server.  I do ve to add XP users to allow them to print.

Most xp machines do have "guest" account that is used by casual visitors at home, however, they could not print on the printer attached to ubuntu server.

If I follow this, and add the "guest" account, will anybody logging in on the xp machine as "guest"  be able to print on the printer attached to ubuntu server?

thanks in advance.

---

### Post by jcfisher on 2007-10-30
I've had the same problem as balance07 - that is, when I try to switch user into the password-less account, the account cannot be unlocked.  Has anyone solved that problem?

---

### Post by Parama on 2007-11-09
> **aysiu said:**
> I think you're looking for something *beyond* a passwordless login. You're looking for a kiosk mode:
[Lock down the GNOME desktop with Pessulus](http://www.linux.com/feature/62060)


Ahaa! This kiosk mode with Pessulus has just made my week! :popcorn: Thank you so much. It works like a charm. Now I just need to fix some way to start up the Epiphany browser automatically when the user logs on and then disable all the panels.

---

### Post by 99bluefoxx on 2007-12-21
can i change the ```
sudo nano -B /etc/shadow
```
to ```
sudo gedit -B /etc/nano
``` with the same result? i find the "nano" editor to be rather confusing

---

### Post by aysiu on 2007-12-21
> **99bluefoxx said:**
> can i change the ```
sudo nano -B /etc/shadow
```
to ```
sudo gedit -B /etc/nano
``` with the same result? i find the "nano" editor to be rather confusing
```
gksudo gedit /etc/shadow
``` would be the correct way to do it.

---

### Post by 99bluefoxx on 2007-12-21
ok, tyvm

---

### Post by balance07 on 2007-12-21
actually, ausiu, you're forgetting the '-B' switch (which doesn't exist for gedit).

try this, 99bluefoxx:

```

sudo cp /etc/shadow /etc/shadow.bak
sudo gedit /etc/shadow

```

---

### Post by aysiu on 2007-12-21
> **balance07 said:**
> actually, ausiu, you're forgetting the '-B' switch (which doesn't exist for gedit).

try this, 99bluefoxx:

```

sudo cp /etc/shadow /etc/shadow.bak
sudo gedit /etc/shadow

```
I did leave out the -B switch, but I believe Gedit's default behavior is to automatically make a backup copy.

---

### Post by °°huygens°° on 2008-01-04
Hi all,
thank you aysiu for this useful tip (and not easy to find by google). :wink:

But, now I only have to hit <enter> in the logon screen.
Given this, Isn't there a method to skip this useless logon screen ? :rolleyes:

Tx

---

### Post by psylem on 2008-01-15
I'm sure there is a way in Gnome, but I'm using Kubuntu so the instructions will differ.

In System Settings, click on the Advanced tab and then the Convenience tab. All the good stuff is on there.

---

### Post by Niniel on 2008-01-15
You can autolog yourself in.

---

### Post by aoakley on 2008-01-21
> **jcfisher said:**
> I've had the same problem as balance07 - that is, when I try to switch user into the password-less account, the account cannot be unlocked.  Has anyone solved that problem?

I am also getting this problem.

To reproduce:

* Add a new desktop user called guest
* Change the encrypted password for guest in /etc/passwd to:
U6aMy0wojraho
* Log in as Guest with no password (just press return for password)
* Use the user session switcher to switch to your original account
* Use the user session switcher again to switch back to the Guest account
* Guest account session is locked and cannot be unlocked- pressing return for password is rejected.

At the moment, the only way to unlock the guest account is pretty drastic, such as restarting GDM, which logs out ALL desktop sessions and restarts X, clearly not a good solution.

Any help much appreciated, thanks.

---

### Post by Craftkiller on 2008-01-21
THANKYOU, this solved my problem with getting my minimyth frontend to connect to my ubuntu backend for remote ssh execution, you are a god!:twisted:

---

### Post by dls156 on 2008-01-27
Aysiu,

VERY NICE! I'm fairly new to Linux and would have never thought of that (even though I just used the live CD to put Ubuntu on my first box a couple days ago). I was trying to figure out a way to do this so my two little ones could log on and not have to enter a complex (or any) password. This worked like a champ!

The only other thing I would throw out here for newb's like me is to modify the folder permissions of any other home folders that you want to keep private (no viewing) so your guest's aren't rummaging around where they don't need to be.  Thanks again Aysiu!

---

### Post by dummyhead3 on 2008-03-13
> But, now I only have to hit <enter> in the logon screen.
Given this, Isn't there a method to skip this useless logon screen ?

Indeed, in System>Administration>Login screen>Security tab>check enable automatic login

Or something like that (my ubuntu is in spanish ;)

---

### Post by o-gforce on 2008-08-04
I love it. Thanks

---

### Post by TiGR on 2008-09-09
> **aoakley said:**
> * Log in as Guest with no password (just press return for password)
* Use the user session switcher to switch to your original account
* Use the user session switcher again to switch back to the Guest account
* Guest account session is locked and cannot be unlocked- pressing return for password is rejected.

Don't use session switcher, use hotkeys instead (alt+ctrl+f7/f8/f9/whatever).

---

### Post by dany linuxnoob on 2008-11-26
I did something stupid and now i cant log into my main account...

I think i erased or added a ":" at the end of the line containing the code of my own password... or a space or something. Help???

---

### Post by aysiu on 2008-11-26
Boot into recovery mode, drop to a root shell, and then type ```
nano -B /etc/shadow
``` When you're done fixing the file, save (Control-X, Y, Enter) and then type ```
exit
```

---

### Post by Penguin Guy on 2009-04-13
Why is this so dangerous? Surely a quick [COLOR="DimGray"]cp /etc/shadow /etc/shadow.backup[/COLOR] would do the trick? Then if something went wrong you could easily boot from a live CD and do [COLOR="DimGray"]mv /etc/shadow.backup /etc/shadow[/COLOR]. Please correct me if I'm wrong. Also is it okay to use any text editor you want or is there a specific reason for using Nano?

---

### Post by aysiu on 2009-04-13
> **Penguin Guy said:**
> Why is this so dangerous? Surely a quick [COLOR="DimGray"]cp /etc/shadow /etc/shadow.backup[/COLOR] would do the trick? Then if something went wrong you could easily boot from a live CD and do [COLOR="DimGray"]mv /etc/shadow.backup /etc/shadow[/COLOR]. Please correct me if I'm wrong. Also is it okay to use any text editor you want or is there a specific reason for using Nano?
It isn't dangerous for you. It's only dangerous if you don't know what you're doing. Clearly you do know what you're doing.

And I chose nano, because that works for Ubuntu, Kubuntu, and Xubuntu. It's okay to use any text editor.

---

### Post by Penguin Guy on 2009-04-13
Okay then, I will try it now: *tries it* It worked - thanks for the guide!
__________________
If nothing = U6aMy0wojraho, what do *two* nothings equal?

---

### Post by crjackson on 2009-04-13
aysiu - How does this affect the keyring manager with regards to wireless? Will the user still need to enter a keyring password or a wireless password? Is there a way to eleminate that too?

---

### Post by aysiu on 2009-04-13
> **crjackson said:**
> aysiu - How does this affect the keyring manager with regards to wireless? Will the user still need to enter a keyring password or a wireless password? Is there a way to eleminate that too?
This is a completely different thing. This is for blank user passwords, not blank keyring passwords.

You can blank the keyring password, too, but [that's a separate process](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14).

---

### Post by Dr_Willis on 2009-04-25
I read this and thought.. I never had to do anything  that complex to get a guest with no password before..  I just do the following in /etc/shadow


[B]guest::14359:0:99999:7:::
[/B]


ie: the password field is empty. 

seems to work for me fine. Any differanes vs the  'encrypted empty' password used in this thread? This way seems a lot easier. 

:lolflag:

---

### Post by steve19137 on 2009-12-03
thanks! it worked great! i got it to work for two accounts, and now my brother and sister can play their windows games (through wine), and allow me to have my version of crack! (aka ubuntu)

---

### Post by leorolla on 2009-12-09
[]("http://ubuntuforums.org/member.php?u=31248")Dr_Willis' solution worked fine for me witu Ubuntu 9.10

---

### Post by nilsja on 2010-08-23
does this also work for an admin user? to recover my lost user1 password?

---

### Post by aysiu on 2010-08-23
> **nilsja said:**
> does this also work for an admin user? to recover my lost user1 password?
If you lost your admin user password, you should reset it using these instructions:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by leorolla on 2010-08-30
> **Dr_Willis said:**
> I read this and thought.. I never had to do anything  that complex to get a guest with no password before..  I just do the following in /etc/shadow


[B]guest::14359:0:99999:7:::
[/B]


ie: the password field is empty. 

seems to work for me fine. Any differanes vs the  'encrypted empty' password used in this thread? This way seems a lot easier. 

:lolflag:

 I just found out in 10.04 that it doesn't work for terminal logins. Better use the magic U6aMy0wojraho :)

---

### Post by vase070 on 2010-11-21
i have 3 users (accounts)  on my pc if i make the password blank on one of them at the login screen when it asks for the username and password i should just type in the username i hit enter leave password box blank right or this only works on pcs with one user on them

---

### Post by sisco311 on 2010-11-21
> **vase070 said:**
> i have 3 users (accounts)  on my pc if i make the password blank on one of them at the login screen when it asks for the username and password i should just type in the username i hit enter leave password box blank right or this only works on pcs with one user on them

Hmmm, this is an old thread. If you want to allow a user to log in without a password, add it to the **nopasswdlogin** group.

Either via the GUI (System -> Administration -> Users and Groups -> *select the user* -> **Password... Change...** -> and select **Don't ask for password on login**) or open a terminal and run:
```

sudo gpasswd -a **username** nopasswdlogin
```
replace **username** with the login name of the user

Users who are not members of the nopasswdlogin group will still require to enter their password for logging in.

---

### Post by vase070 on 2010-11-22
does this work for ubuntu (edubuntu) 7.04 feisty fawn

---

### Post by sisco311 on 2010-11-22
> **vase070 said:**
> does this work for ubuntu (edubuntu) 7.04 feisty fawn

Nope, not by default. In Hardy and earlier versions you have to edit /etc/pam.d/gdm to look like this:```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
**auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin**
...

```
and create the nopasswdlogin group:
```
sudo addgroup --system nopasswdlogin
```

EDIT: If you want to use aysiu's method, then instead of manually editing the shadow file, you could use usermod to change the user's password:
```
sudo usermod -p 'U6aMy0wojraho' **guest**
```
where **guest** is the login name of the user.

---

### Post by vase070 on 2010-11-22
> **sisco311 said:**
> Nope, not by default. In Hardy and earlier versions you have to edit /etc/pam.d/gdm to look like this:```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
**auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin**
...

```and create the nopasswdlogin group:
```
sudo addgroup --system nopasswdlogin
```EDIT: If you want to use aysiu's method, then instead of manually editing the shadow file, you could use usermod to change the user's password:
```
sudo usermod -p 'U6aMy0wojraho' **guest**
```where **guest** is the login name of the user.
 
well that is what i mean i was asking if [[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")'s method of making a user passwordless works on ubuntu 7.04 yo know by configuring the shadow file and all that other stuff that is what i was asking :D Tnx anyway :D

---

### Post by sisco311 on 2010-11-22
> **vase070 said:**
> well that is what i mean i was asking if [[COLOR=#D40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")'s method of making a user passwordless works on ubuntu 7.04 yo know by configuring the shadow file and all that other stuff that is what i was asking :D Tnx anyway :D

D'oh! Yes, aysiu's method should work in any version of Ubuntu and in most Linux and Unix distributions.

---

### Post by vase070 on 2010-11-22
with the help of [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941")'s method and this video you can hack any ubuntu-linux (gnome) pc system you just have to know what you are doing have fun and thanks i learned a lot about ubuntu:):):) [http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded](http://www.youtube.com/watch?v=AkENYv7kEhg&feature=player_embedded)

---

### Post by shvahabi on 2011-03-26
The same task via graphical method.
This short tutorial may be useful for those who prefer to use a GUI. I successfully tested it for Lucid Lynx (Ubuntu LTS 10.04):
[LIST=1]
[*]Main_Menu>>System>>Administration>>Users_and_Groups
[*]Click on "**Add**" button to create a new user
[*]Select the newly created user shown on left pane
[*]Click on the "**Change...**" button opposite to password
[*]Check the "**Don't ask for password on login**" option on the just appeared dialog box.
[/LIST]

---

### Post by sieve on 2011-04-03
Thanks, this worked perfectly


*Open /etc/shadow: gksudo gedit /etc/shadow
*Find the line that starts with the user you just made. Notice the line has multiple fields separated by colons.
*Change the second field to: U6aMy0wojraho. In my case:
name:$6$m4CpcgBw$i9XLGaUNToClOJ1X5Grug/COUjlkhoPv1:15048:0:99999:7:::
becomes:
name:U6aMy0wojraho:15048:0:99999:7:::
*Save the file, log out, and try your new password-less account.

The origin of this method is from the Ubuntu livecd. The default user (ubuntu) requires no login password. If you look at /etc/shadow on the livecd, U6aMy0wojraho is the encrypted form of the magic password used.

---

### Post by conradin on 2011-06-21
I Thought for sure that would break my system but it worked! I'm very happy with this insight!

---

### Post by rountrey on 2011-09-12
Does this only work with systems that have a GUI? I have an old HP thin client that has command line only on it (10.04) and I can't get it to work. I've tried editing the shadow, tried using passwd, even deleted the password and it still asks for a password. I am doing this through ssh because I don't have a monitor or keyboard hooked up it. 

Thanks.

NEVER MIND, i forgot to allow blank passwords in sshd_config

---

### Post by private_lock on 2011-10-06
Works great ... just a sidenote:

After creating the guest account, you should log into the guest at least once with the password provided at creation. I was required to change the initial password on first login. If you already wiped out the password by editing /etc/shadow, you'll have to do it all over again.

Moreover KDM (Kubuntu-login-screen) has a bug. I get the mandatory prompt to change the initial password. But I cannot type into any of the text fields (maybe, it just doesn't echo stars for the letters I type ... extremly confusing). To work around, switch to a text console with ctrl+alt+f1 and log in as guest, change the password, exit and go back to the graphical screen with ctrl+alt+f7 or ctrl+alt+f8 whichever it was.

Thanx
private_lock

---

### Post by MarkoHF on 2012-01-25
Well, it doesn't work for admin account. Once you login to the admin account with the guest method (sysadmin or netadmin) you can use the features as it says incorrect password.

---

