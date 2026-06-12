---
title: "Tried everything, can't add computer to Ubuntu One"
date: 2010-10-21
forum: Ubuntu One (CLOSED)
---

### Post by JaredFactley on 2010-10-21
I've been using Ubuntu One for a short time now. Eventually had a problem where the context menu wasn't there in Nautilus. Found others with the same problem, and the solution was to uninstall/reinstall. So I did.

Now under devices, only thing listed is <Local Machine>. 
I have set Firefox as the default browser, but it does not open to let me choose my computer. 

I have no token entries in Passwords and Encryption for Ubuntu One.

I've tried the work arounds that are supposed to force it to open, but still nothing.

Is there anything I'm missing?

---

### Post by JaredFactley on 2010-10-22
Nobody has any idea? I emailed customer support, but haven't received a reply.

---

### Post by onaridge on 2010-10-22
I am having the exact same problem. 2 years later.

---

### Post by JaredFactley on 2010-10-23
Well, that isn't very reassuring.

---

### Post by duanedesign on 2010-10-23
What version of Ubuntu are you using?

I will assume Maverick.

Can you try the following and let us know the results?

   1. Quit the Ubuntu One Preferences
   2. Open System->Preferences->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open a Terminal and run the command:
```
        killall ubuntu-sso-login; u1sdtool -q; u1sdtool -c
```
   9. a window should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

If you are on Lucid the steps are the same but the Password and Encryption Keys is under Applications > Acdcessories > Password and Encryption Keys. And ubuntu-sso-login is ubuntuone-login. Lastly Lucid opens a webpage to add your computer, Maverick does not use the browser anymore.

Also if you are on Lucid try this command and see if it works:

```
xdg-open http://www.google.com
```

let us know how it goes.

~duanedesign

---

### Post by JaredFactley on 2010-10-24
Yeah, I've seen these same instructions numerous places, and tried them numerous times.

I just gave it a shot again. Like I said, there's no U1 Token in my passwords.
And when I go to the site, my computer isn't listed. That's my problem. it just says 'You haven't added any computers or devices to your Ubuntu One account. To get started please visit the installation details.'

And when I enter the command in terminal no window opens. Browser or otherwise.

Thanks for the help though.

Edit: I'm using 10.10 by the way.

---

### Post by promet on 2010-10-25
I'm not sure if this will be useful, but I was having a devil of a problem getting UbuntuOne to work in Maverick. I was fiddling around with my password tokens in Seahorse, the UbuntuOne applet and so on.

As it turns out, it was my password format that was the problem. I signed up for Ubuntuone when it first came out and signed up with a very basic password. (I think) since then they've placed a security minimum on passwords for Ubuntuone, i.e. "Must be at least 8 characters long, and have at least one capital letter and one number". My account password had neither.

So, I:


[LIST]
[*] Used Seahorse (Password and Keys Manager) to erase by "UbuntuOne" entry in the passwords tab of that app.
[*] Logged into the [UbuntuOne website]("https://one.ubuntu.com/") and changing my account password there to something more secure and nerdy that matched the above requirements.
[*] Restarted the UbuntuOne applet, and it prompted me to sign in, at which time I entered the new password, and it let me right back in.
[/LIST]
   
**NOTE:** If the third "applet step" is not getting you another login attempt, try running the command from the terminal, i.e.:

```
u1sdtool -c
```That has worked for me, and I hope it may of some use to you guys as well.

Cheers

---

### Post by aboud on 2011-09-06
I am sorry Ubuntu One, there is no way I can get this working. tried all of the above. Hopelessly ( I am going back to Dropbox.

---

