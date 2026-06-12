---
title: "I lost my root password"
date: 2009-05-05
forum: Security
---

### Post by Vostrocity on 2009-05-05
-=SOLVED=- (I don't know what's the formal way to close threads..)

I've only been using Ubuntu for about 3 weeks, but for some reason my root password has changed itself to something that I don't know of. I certainly don't remember ever messing with it, I don't even know how. :confused:

I first ran into this problem when I was trying to force mount a drive. ([link]("http://ubuntuforums.org/showthread.php?t=1129677&page=2"))

[QUOTE=Vostrocity][QUOTE=thatcooldude]Have you set a root password before?  Try issuing the following command in your Terminal:

```
sudo passwd
```

Type in a desired root password, then confirm it.

Then try the sudo command you were attempting before and you should be able to mount the drive successfully.  You're correct - the error you're receiving has to do with the password and not the command.  I would hold off on reformatting until you've exhausted your other options!

Please post back and let me know if setting the password works![/QUOTE]

Here's what I get.
```

andrew@Vostrocity:~$ sudo passwd
[sudo] password for andrew: 
testingSorry, try again.
[sudo] password for andrew: 
testtestSorry, try again.
[sudo] password for andrew: 
testing againSorry, try again.
sudo: 3 incorrect password attempts
andrew@Vostrocity:~$ testing again

```
And that's the exactly what happens when I get the problem in the first place. :confused:[/QUOTE]

[QUOTE=thatcooldude]Then it looks like the problem is your root password has been set to something you no longer know :/

Try resetting your root password then retry your previous commands.
[http://www.wallpaperama.com/forums/how-to-reset-linux-root-forgotten-passwords-get-retrieve-root-password-t956.html](http://www.wallpaperama.com/forums/how-to-reset-linux-root-forgotten-passwords-get-retrieve-root-password-t956.html)[/QUOTE]

So here's where I have the problem. When I'm doing the special boot described in the link, I get to one of those old 8-bit text based screens (and this is happening before the Ubuntu loading screen). There are several options, one of which is "root". So I type "root" and the option gets highlighted, but then I can't figure out how to enter it. I've tried it three times already. I might just be really dumb.. :(

---

### Post by Dr Small on 2009-05-05
Why do you need a root shell? Can't you just use either of these?
```
sudo -i
sudo su
```

---

### Post by cariboo on 2009-05-06
When setting a password, you need to specify a user eg:

```
sudo passwd andrew
```

---

### Post by JK3mp on 2009-05-06
Sometimes you need to set a passwd to be root, by default it sets it null or something (best way i can describe it,lol). But sudo and the password for your account should work for the mounting the drive.

---

### Post by cdenley on 2009-05-06
You don't need and shouldn't have a root password.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> **JK3mp said:**
> Sometimes you need to set a passwd to be root, by default it sets it null or something (best way i can describe it,lol). But sudo and the password for your account should work for the mounting the drive.

You don't need to set a password, the default password hash of "!" shouldn't prevent you from using the root account in any way (except authenticating). Setting the root account's expiration date to something in the past (another account disabling method) may give you problems, though.

```

andrew@Vostrocity:~$ sudo passwd
[sudo] password for andrew: 
testingSorry, try again.
[sudo] password for andrew: 
testtestSorry, try again.
[sudo] password for andrew: 
testing againSorry, try again.
sudo: 3 incorrect password attempts
andrew@Vostrocity:~$ testing again

```
You are being prompted for the password for the user "andrew", not root. Did you forget that password? Did you type "testing" and "testtest"?

> 
There are several options, one of which is "root". So I type "root" and the option gets highlighted, but then I can't figure out how to enter it. I've tried it three times already. I might just be really dumb.

Use the arrows to select "root shell prompt" (I think it's called), then press "enter". Once you have a root shell prompt, reset the password for your admin user (if you forgot it):
```

passwd andrew

```

---

### Post by bigbearomaha on 2009-05-06
[http://www.handlewithlinux.com/10-ways-of-resetting-a-lost-linux-root-password](http://www.handlewithlinux.com/10-ways-of-resetting-a-lost-linux-root-password)

---

### Post by Vostrocity on 2009-05-06
> **Dr Small said:**
> Why do you need a root shell? Can't you just use either of these?
```
sudo -i
sudo su
```

I don't know actually. I haven't been using Linux for long so I'm not familiar with all that.


> **cdenley said:**
> You don't need and shouldn't have a root password.

You are being prompted for the password for the user "andrew", not root. Did you forget that password? Did you type "testing" and "testtest"?

That's actually a good point. I don't know why I was thinking about changing the root password. But the thing is, I did type in my account password, and it just doesn't work. Of course I was only typing "testing" so wouldn't have to show everyone. But the exact thing happens when I type in my password correctly.


> **cdenley said:**
> Use the arrows to select "root shell prompt" (I think it's called), then press "enter". Once you have a root shell prompt, reset the password for your admin user (if you forgot it):
```

passwd andrew

```

That was the problem I had actually. I could select the option but pressing enter does nothing.. :confused:

---

### Post by bodhi.zazen on 2009-05-06
> andrew@Vostrocity:~$ sudo passwd[FONT=monospace]
[/FONT][sudo] password for andrew:[FONT=monospace]
[/FONT]testingSorry, try again.The system is asking for your users password :

> [sudo] password for [SIZE=2]**andrew**[/SIZE]:NOT ROOT 's

[uwiki]RootSudo[/uwiki]

As has been pointed out, you almost never need to set a root password, use :

```
sudo -i
```

---

### Post by wirelessmonkey on 2009-05-06
You should not Ever need to set root's password, and Marvin666, it is against forum policy to post instructions for doing so.

---

### Post by cdenley on 2009-05-07
> **Vostrocity said:**
> I don't know actually. I haven't been using Linux for long so I'm not familiar with all that.




That's actually a good point. I don't know why I was thinking about changing the root password. But the thing is, I did type in my account password, and it just doesn't work. Of course I was only typing "testing" so wouldn't have to show everyone. But the exact thing happens when I type in my password correctly.




That was the problem I had actually. I could select the option but pressing enter does nothing.. :confused:

So enter doesn't work in the recovery mode menu, and when you try to run sudo, your password is echoed to the terminal because it thinks you already entered a password and is attempting to authenticate you already? This sounds like a keyboard problem to me. Sudo doesn't print your password as you type it, unless it thinks you already entered it.

---

### Post by Vostrocity on 2009-05-07
> **bodhi.zazen said:**
> The system is asking for your users password :

NOT ROOT 's

[uwiki]RootSudo[/uwiki]

As has been pointed out, you almost never need to set a root password, use :

```
sudo -i
```

> **wirelessmonkey said:**
> You should not Ever need to set root's password, and Marvin666, it is against forum policy to post instructions for doing so.

Yeah I realized that in post #7.
> That's actually a good point. I don't know why I was thinking about changing the root password. But the thing is, I did type in my account password, and it just doesn't work. Of course I was only typing "testing" so wouldn't have to show everyone. But the exact thing happens when I type in my password correctly.



:)
> **cdenley said:**
> So enter doesn't work in the recovery mode menu, and when you try to run sudo, your password is echoed to the terminal because it thinks you already entered a password and is attempting to authenticate you already? This sounds like a keyboard problem to me. Sudo doesn't print your password as you type it, unless it thinks you already entered it.

Thank you! That solved it! I didn't know that sudo doesn't print your password, so when I was trying to type it in and it didn't show up I always just entered to the next line first. 
:)

---

