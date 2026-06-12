---
title: "Lost passwords"
date: 2010-01-09
forum: Security
---

### Post by Hopalong on 2010-01-09
I appear:o to have been blitzed! I have 9.10 and 8.10 installed: my passwords for each of them no longer work. (I've come in here from a CD.)
  How can I reset my passwords? Can it be done without reinstalling?

---

### Post by cariboo on 2010-01-09
Please use the search function before asking a question, this has been asked and answered several times. That being said start in recovery mode, when you get to the menu, select drop to root prompt. Once at the prompt type:

```
passwd <usrname>
```

where <username> is your user name.

---

### Post by Hopalong on 2010-01-10
Sorry to appear in such a rush last time. I have now perused the security forum. and found your reply once earlier. However there is more to this than meets the eye! I have a dual boot Grub with 8.10 and 9.10. Trying your fix on 9.10 appeared not to work, so I reinstalled it from disk. That got me into the system, but I still could not authenticate the mount of my data partition  I tried on the original 8,10, and got the same effect.
   I then played with the partition names, and behold, 9.10 as reinstalled now works a treat. But 8.10 will not take the new password to authenticate the mount! 
  Any ideas as to what's afoot? I don't wnat to have to reload 8.10 as well.
(Yes its all backed up to couple of USB sticks and a CmNbook if necessary!)

---

### Post by cariboo on 2010-01-10
So your question really had nothing to do with lost passwords, as your password still worked, but you couldn't mount a partition?

How are you trying to mount your partition do use use something like this?

```
sudo mount /dev/sda2 /media/disk
```

or by disk label?

```
sudo mount /dev/my hard drive /media/disk
```

If your drive label has spaces in the name, either enclose the name in quotation marks **"my hard drive"** of use the back slash to delimit the spaces **my\hard\drive**.

---

### Post by Hopalong on 2010-01-11
The procedure I use goes like this:
   Places
   Computer
   Double click 'UserData' the name I gave my data partition
   In the resulting panel, enter my password and click 'Authorise'
   I the get a message saying it failed.
If I try and  type in 'terminal' it wants authorisation, which also fails.
  Is this normal behaviour for 8.10? I don't remember any such palaver before I created the data partition (which I did in 9.10).I am suspicious that a hacker has been at this system. ( I note that SSH is installed in 9.10: I can't find out if it is in 8.10 because I can't get authorisation to use Synaptic!)

---

### Post by cariboo on 2010-01-11
It sounds like you aren't in the admin or adm groups. Open a terminal and type:

```
groups
```

the output should look something like this:

```
groups
me adm dialout cdrom plugdev lpadmin admin sambashare
```

I substituted me for my user name. If **adm** or **admin** are missing from your list. you'll have to start in recovery mode and once at the prompt type:

```
gpasswd -a <username> adm
```

or 

```
gpasswd -a <username> admin
```

whichever one is missing. <username> = your user name.

---

### Post by Hopalong on 2010-01-12
The output from 'groups' is exactly as you listed - they're all there.
It seems to me that, in 8.10, wherever the mount looks for the password is different from where the password changes went, and is either a messed up password, or even empty. Is this a possibility?
  Any time now I shall completely backup from 8.10 and reinstall it, or do without it. But it might be a pity not to chase this problem to its cause? If you think I should forget it and leave you in peace, do say so: I sha'n't be offended.

---

