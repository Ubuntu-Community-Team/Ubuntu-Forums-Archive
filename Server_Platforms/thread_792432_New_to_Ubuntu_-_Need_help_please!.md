---
title: "New to Ubuntu - Need help please!"
date: 2008-05-12
forum: Server Platforms
---

### Post by Overwhelmed on 2008-05-12
Hello,

First of all, I need to let you all know that I am completely new to Ubuntu (or any other Linux distro for that matter).

I have wanted to escape from Microsoft for a long time now, but have been hesitant about learning a whole new OS; considering I am comfortable with using Windows, despite my dislike for Microsoft.

I am the "computer guy" at work, and I have a fair amount of programming experience as well as some basic network admin stuff.

Nevertheless, when my boss asked me to install a file server computer for the office, I figured it would be a great opportunity to finally dive into Linux. After some Google research, I concluded that Ubuntu Server would be best to accomplish the job and learn.

Therefore, I fully expect to have many questions, and have no doubt that a few will be pretty basic (if not outright stupid).

I already have come across a problem and I have not even got into Ubuntu yet...

I installed Ubuntu and everything seemed to go perfect. However, when I reboot and get to the prompt "serverhost login:" (serverhost is the name I gave during installation) I can not log in.

When I entered the server name, there was no prompt for a password.

I tried entering 'sudo passwd root' but it gave me a "Login incorrect" message.

During installation I also entered a non-root account name ("nonroot") and a user nae for the account ("nruser"); I tried these at the login promt, but as expected they did not work.


How do I get passed the login prompt for "serverhost"?
(*also, for each login name I try, when the password prompt comes up, nothing happens as I type. Should it show a * or something as I type?)


I appreciate the help and apologize for being so clueless.

---

### Post by tamoneya on 2008-05-12
what did you put in for the username when it asked "serverhost login:" Did you put nruser or non-root.

---

### Post by MaindotC on 2008-05-12
Hi, Overwhelmed.  I'm not familiar with Ubuntu Server but it should just be Ubuntu with server packages installed.  If you want to try resetting the password, try:

Pressing esc at the grub prompt.
Press e for edit.
Highlight the line that begins kernel <kernel number>, press e
Go to the very end of the line, add rw init=/bin/bash
Press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
Type in passwd <username>. Set your password.
Type in reboot.

---

### Post by Overwhelmed on 2008-05-12
> **tamoneya said:**
> what did you put in for the username when it asked "serverhost login:" Did you put nruser or non-root.

I tried both nonroot and nruser. Both without password and both with using the other as the password.

I tried blank for both as well.

Is the login supposed to be he non-root account and/or name that I entered?

When the password prompt comes up, is the cursor supposed to move as I type? (because it does not).

---

### Post by MaindotC on 2008-05-12
If I use ctrl + alt + f2 and login the cursor moves for the username login, but it does not for the password.

---

### Post by Overwhelmed on 2008-05-12
> **strAlan said:**
> Hi, Overwhelmed.  I'm not familiar with Ubuntu Server but it should just be Ubuntu with server packages installed.  If you want to try resetting the password, try:

Pressing esc at the grub prompt.
Press e for edit.
Highlight the line that begins kernel <kernel number>, press e
Go to the very end of the line, add rw init=/bin/bash
Press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
Type in passwd <username>. Set your password.
Type in reboot.
Thanks for the reply...

Which <username> do I use?

serverhost (the name of the server)
nonroot (the non-root account name)
nruser (the non-root account user name)

or do i enter a new user name and password?

---

### Post by MaindotC on 2008-05-12
If you remember any of the usernames, you can choose any of them to enter in this field - even the root user.  If that's not working for you and for kicks you want to create a new user, you can type:

```

useradd <new_user_name>
#then to set a password
passwd <new_user_name>

```

---

### Post by Overwhelmed on 2008-05-12
> **strAlan said:**
> Hi, Overwhelmed.  I'm not familiar with Ubuntu Server but it should just be Ubuntu with server packages installed.  If you want to try resetting the password, try:

Pressing esc at the grub prompt.
Press e for edit.
Highlight the line that begins kernel <kernel number>, press e
Go to the very end of the line, add rw init=/bin/bash
Press enter, then press b to boot your system.
Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
Type in passwd <username>. Set your password.
Type in reboot.
Thank you strAlan, it worked! :)

I used nruser because it seemed the most obvious and entered a password. After reboot I was able to log in easily.

Now I have to keep reading and figure out what to do next.

I came across a site that shows how to load the Ubuntu desktop UI into the Server edition I think I will try that next.

Thanks again for your help.

---

### Post by MaindotC on 2008-05-12
Star me :)

---

### Post by cdtech on 2008-05-13
This is the site I followed to get me going on my server. Just a thought...

[[COLOR="DarkRed"]The perfect setup[/COLOR]]("http://howtoforge.com/perfect_setup_ubuntu_6.06")

---

### Post by Mr_Whippy on 2008-05-13
theres a newer version of that link for 8.04lts,

[The Perfect Setup]("http://howtoforge.com/perfect-server-ubuntu8.04-lts-p3")

---

### Post by cdtech on 2008-05-13
> **Mr_Whippy said:**
> theres a newer version of that link for 8.04lts,

[The Perfect Setup]("http://howtoforge.com/perfect-server-ubuntu8.04-lts-p3")

Thanks for that link Mr. Whippy. It's been a long time from 6.06. :)

---

