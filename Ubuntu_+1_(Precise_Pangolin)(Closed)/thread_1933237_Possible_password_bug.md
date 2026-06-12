---
title: "Possible password bug?"
date: 2012-02-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by go7Ul1ai on 2012-02-28
I think I'm experiencing a rather annoying bug, I wanted to change the settings so that instead of typing in a password at login I would just click to login instead. This works fine, however the system doesn't recognise my password when the prompts appear (when using sudo in terminal and update manager etc).

This is what I did:

System Settings > User Accounts > Unlock

I then clicked 'password' and selected 'click to login', and this is where the problem started.

I can't change back as I can't unlock it, it doesn't even accept when I select a different user and enter their password either.

So is this a bug, or am I an idiot?

---

### Post by go7Ul1ai on 2012-02-29
Thanks again guys

---

### Post by ventrical on 2012-02-29
> **lee.jarratt said:**
> Thanks again guys

 Did they fix that bug?

---

### Post by ventrical on 2012-02-29
> **lee.jarratt said:**
> I think I'm experiencing a rather annoying bug, I wanted to change the settings so that instead of typing in a password at login I would just click to login instead. This works fine, however the system doesn't recognise my password when the prompts appear (when using sudo in terminal and update manager etc).

This is what I did:

System Settings > User Accounts > Unlock

I then clicked 'password' and selected 'click to login', and this is where the problem started.

I can't change back as I can't unlock it, it doesn't even accept when I select a different user and enter their password either.

So is this a bug, or am I an idiot?

  I think then  that we would approach this with trepidation because none of us want to get locked out of our systems in that way, so, thanks for the heads up :)

---

### Post by go7Ul1ai on 2012-02-29
> **ventrical said:**
> Did they fix that bug?

I'm afraid the bug hasn't been fixed, I guess I should go report it? The bug has been present for a while and is consistent, I've formatted and re-installed Precise 5+ times now to only run into the same issue of being locked out of the system.

---

### Post by cariboo on 2012-02-29
Why don't you set auto-login when you do an install? The option is right there when you create your username, computer name and password.

---

### Post by go7Ul1ai on 2012-02-29
> **cariboo907 said:**
> Why don't you set auto-login when you do an install? The option is right there when you create your username, computer name and password.

Because my partner also uses the same machine. And also, are you saying we should just forget that this bug exists and just work around the problem?

---

### Post by cariboo on 2012-02-29
Of course you shouldn't forget about the bug, I'm just trying to understand, what it is you are trying to do. Do you see what I do when elevating privileges? See the screenshot

---

### Post by effenberg0x0 on 2012-03-01
I can't find it. Have a look at this screenshot:

[B]OO vs. PP: SystemSettings->Accounts->Password - Where's "Click to Login"?
[/B][ATTACH]213526[/ATTACH]

I'm willing to help testing it and specially interested in finding a way out of it that needs no reinstall, as well as +1 in a bug report about it but, so far, I can't even understand how it's done. I'd appreciate better directions if possible. 

Regards,
Effenberg

**EDIT:** AH, I see how you did it. I tested it and in fact you can't change it back without a password. I have tested OO and PP. It is clearly a bug IMO. If you haven't yet, create a bug report and give us a link here so we can +1. But, just to help you avoid reinstalling, here's a 1-minute workaround:

**1)** Restart the PC and Hold **Shift** to see GRUB Options
**2)** Select the Recovery Option (Typically the second one) and, when asked, select "**Root (Drop to root shell prompt)**"
**3)** Remount RW, so /etc/shadow is writable.
```
mount -o remount,rw /
```**4)** Create a new password for your user:
```
passwd <your-user>
```You'll see this:
> 
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
**5)** Press "**Ctrl+D**" and select **Resume** when asked

That's it, you're back in the game.

Regards,
Effenberg

[B]EDIT2: If others want to test it before +1'ing the bug report, it's obviously 100% safe to recover, as long as you can root shell via Grub Recovery or if you have a secondary user (sudoer) in the machine. It takes two minutes tops to test/recover.
[/B]

---

### Post by ventrical on 2012-03-01
Thats why I originally did not reply .. because I could not see how to replicate the bug.

---

### Post by ventrical on 2012-03-01
> **lee.jarratt said:**
> I'm afraid the bug hasn't been fixed, I guess I should go report it? The bug has been present for a while and is consistent, I've formatted and re-installed Precise 5+ times now to only run into the same issue of being locked out of the system.


Hi Lee,

 I guess effenberg found the work arounmd for this , but, initially I could not see how to  found the bug (how it was explained) , but, I guess they found it now.

---

### Post by effenberg0x0 on 2012-03-01
@Ventrical, 
I should have been more *Precise* in my previous post. Here's how I did it:

Dash -> System Settings-> User Accounts
Click "Unlock", Enter your password.
Click on the Password Asterisks.
Select action "Login without a password" and press "Change".
Close the User Accounts dialog.

Now, reopen Dash -> System Settings-> User Accounts and try to undo what you just did. You can't, because, without a password, you can't unlock it. 

Then use the workaround I posted to get the system back.

Regards,
Effenberg

---

### Post by effenberg0x0 on 2012-03-01
The thing is, your user still has a password, but it's encrypted as usual, and you don't know it. Ideally, you should be able to still have your normal password set, but the system would use it to login. The question is, how does that adhere to standard Linux? It doesn't, it's undoable without changes to the way it handles security/passwords.

At this point, if devs do see and acknowledge this bug, I think they will simply remove the option for password-less login, because having this option while not having the user password changed to something else would require too much changes, security concerns, etc.

On the other hand, they could do small changes to warn the user abour what he's doing. 
- Add a warning, like: "This is only reversible via Recovery Root Shell or through a another user account! Proceed?"
- Only offer this option if there's a secondary user (sudoer) in the machine, with an active password. 

Regards,
Effenberg

---

### Post by go7Ul1ai on 2012-03-01
Thanks for the great responses guys, I know I'm not the best at explaining but I'm glad you figured it out and could replicate the bug for yourselves. I am in the process of reporting a bug now.

Edit: Looks like this bug was reported near the middle of last month, I guess the best we could do is mark the bug as effecting you. Thanks for your help guys :-)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/882255](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/882255)

---

### Post by effenberg0x0 on 2012-03-01
> **lee.jarratt said:**
> Thanks for the great responses guys, I know I'm not the best at explaining but I'm glad you figured it out and could replicate the bug for yourselves. I am in the process of reporting a bug now.

Edit: Looks like this bug was reported near the middle of last month, I guess the best we could do is mark the bug as effecting you. Thanks for your help guys :-)

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/882255](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/882255)

Done. Thanks for taking the time to test it and for presenting it to us.

Regards,
Effenberg

---

### Post by mc4man on 2012-03-01
nv

---

### Post by ventrical on 2012-03-01
> **effenberg0x0 said:**
> @Ventrical, 
I should have been more *Precise* in my previous post. Here's how I did it:

Dash -> System Settings-> User Accounts
Click "Unlock", Enter your password.
Click on the Password Asterisks.
Select action "Login without a password" and press "Change".
Close the User Accounts dialog.

Now, reopen Dash -> System Settings-> User Accounts and try to undo what you just did. You can't, because, without a password, you can't unlock it. 

Then use the workaround I posted to get the system back.

Regards,
Effenberg

  I am not questioning the accuracy of your solution and you have been exceptionally clear . I was just trying to kindly point out the original vagueness in the OPs' first post. It was just the way it was worded..  and I could not find that on my system .. but I can see it now and as always .. thanks again!

Regards, Ventrical

---

### Post by ventrical on 2012-03-01
> **effenberg0x0 said:**
> I can't find it. Have a look at this screenshot:

[B]OO vs. PP: SystemSettings->Accounts->Password - Where's "Click to Login"?
[/B][ATTACH]213526[/ATTACH]

I'm willing to help testing it and specially interested in finding a way out of it that needs no reinstall, as well as +1 in a bug report about it but, so far, I can't even understand how it's done. I'd appreciate better directions if possible. 

Regards,
Effenberg

**EDIT:** AH, I see how you did it. I tested it and in fact you can't change it back without a password. I have tested OO and PP. It is clearly a bug IMO. If you haven't yet, create a bug report and give us a link here so we can +1. But, just to help you avoid reinstalling, here's a 1-minute workaround:

**1)** Restart the PC and Hold **Shift** to see GRUB Options
**2)** Select the Recovery Option (Typically the second one) and, when asked, select "**Root (Drop to root shell prompt)**"
**3)** Remount RW, so /etc/shadow is writable.
```
mount -o remount,rw /
```**4)** Create a new password for your user:
```
passwd <your-user>
```You'll see this:
**5)** Press "**Ctrl+D**" and select **Resume** when asked

That's it, you're back in the game.

Regards,
Effenberg

[B]EDIT2: If others want to test it before +1'ing the bug report, it's obviously 100% safe to recover, as long as you can root shell via Grub Recovery or if you have a secondary user (sudoer) in the machine. It takes two minutes tops to test/recover.
[/B]

 How sweet it is ! :)

---

