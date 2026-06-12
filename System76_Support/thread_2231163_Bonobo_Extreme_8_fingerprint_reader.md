---
title: "Bonobo Extreme 8 fingerprint reader"
date: 2014-06-23
forum: System76 Support
---

### Post by michael181 on 2014-06-23
I just recieved a bonx8 and everything is great except I can't figure out how to set up or enable the fingerprint reader.  If you search for it in that Unity search it sends you over to the user set up window but fingerprint isn't an option.  I looked at the quickstart guid (which was just 2 pictures) and I didn't see a link to drivers on the System76 web page. I ran the System76 Driver program and it says everything is up to date.  Any advice?  Thanks!

---

### Post by Vladlenin5000 on 2014-06-24
*subscribed*

---

### Post by michael181 on 2014-06-24
I managed to get it working!  I followed the instructions here: [https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint) and everything seems to be fine; the fingerprint reader was compatable and registered, and it works for logging in and sudo.  The only issue is that when you try to add the repository they tell you to add they say it is out of date.  Ignore that and add it anyway.  Then just follow those steps to register your finger and everything should work.  System76 should definitely include this automatically with their driver software, but at least it works.  Note that all of the instances where you would normally enter a password (except, I think, decrypting your home folder) are replaced with a fingerprint scan, but you should just be able to turn it off again if you want.  Also, if the scan fails you can still use your normal password.

---

### Post by michael181 on 2014-06-24
So having tested it further it seems like sometimes Ubuntu is defaulting to the password rather than the fingerprint reader for no clear reason, but I don't know how to specifically reproduce that yet.  I'll post an update when I have more information.

---

### Post by michael181 on 2014-06-24
I figured out at least the first part of the problem, and it is very weird: it is caused by having 2 (and probably more) monitors.  When you lock your screen (either deliberatly or after a delay) the screen that your mouse was on when this happened asks for you to swipe your finger to log back in.  However, if you go over to your other screen it asks for a password.  Not sure if this has any persistance after you log in but so far it doesn't look like it.

---

### Post by michael181 on 2014-06-27
The fingerprint reader is working inconsistenly when logging back in after sleeping (e.g. closing the lid).  Some times it doesn't come up at all, or sometimes the scanning prompt comes up but it doesn't respond to repeated finger swipes and you have to wait for it to time out to let you use a password.  I'll try to put in a ticket with System76 but this is a work provided laptop so I don't have access to their normal ticketing system.  It would be great to hear from any other owners.

Also, I am no longer sure about the specific issues with two screens.  Now there seem to be times where the screen the mouse was on when the computer locked gets the password login and the other screen gets the finger swipe log in.  Not sure if I need to talk to System76 or the fprint (e.g. free drivers) people about that.

---

### Post by Vladlenin5000 on 2014-06-27
I subscribed to your thread hoping that something new could be found. I have the some Bonobo as you but never tried to enable the fingerprint reader. I used it before in an old notebook and found it unreliable at least since 13.10.
Unfortunately it seems the situation hasn't changed since. Thank you for testing and reporting back, much appreciated. 

Good luck with your ticket. I though about doing the same but actually the fingerprint reader feature isn't that important to me. I bet System76 will just say it's unreliable therefore we opted for not supporting it by default. I guess if they had the option they would have it without fingerprint reader but there only a few things they can 'customize' when they order the barebones from Clevo and others (the Bonobo Extreme 8 is a Clevo).

---

### Post by michael181 on 2014-06-27
Thanks for the info!  For a while I didn't think there was much value to finger print readers but after I got a Samsung Galaxy S5 (which also has a fingerprint reader) I found it so much more conveinient.  When the reader on the bonx8 works it is extremely convenient.  Much faster than a password, especially if you have a long one.  If I have time I may dig into the code and see if I can figure out why this happens.  I think, for the most part, this is not a firmware or hardware issue since it gets messed up by high level things rather than just totally failing to read.  I will post anything else 
I learn here, especially if I make a change that fixes it.

---

### Post by consman on 2014-08-18
Thanks for posting this!  I have this same problem with my Bonobo Extreme since upgrading to 14.04 and I also tried the steps at [https://launchpad.net/~fingerprint/+archive/ubuntu/fprint](https://launchpad.net/~fingerprint/+archive/ubuntu/fprint) , but I my fingerprint scanner is not one of those listed - but rather [COLOR=#000000]147e:1002  :(  so the steps did not work (I tried them anyway) .  This is very frustrating as I purchased the product from System76 less than two years ago, in Dec 2012, partially because I like this feature so much.  It worked great in 12.XX and 13.XX!  
As much as I can tremendously appreciate all of the hard work that goes into a release like 14.04, where the team is operating at a huge disadvantage trying to accommodate so many combinations of hardware, I am going to try to revert. Does anyone else have any advice?  Thanks. [/COLOR]

---

### Post by Vladlenin5000 on 2014-09-02
[https://launchpad.net/~fingerprint](https://launchpad.net/~fingerprint)

---

### Post by consman on 2014-09-09
Thanks, Vladlenin5000! It works great. But I have already reverted to 13.10.  Would this have worked with 14.04  ?

---

### Post by consman on 2015-06-06
Solved!  They have fixed this in 14.04 and these instructions [https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui]("https://launchpad.net/%7Efingerprint/+archive/ubuntu/fingerprint-gui") worked well on my Bonobo Extreme.

Although now I see that as of a few days ago, maybe around 07/08/2015, there are some problems.  The finger print reader works, except when I first start the machine at the initial login prompt. And at other times, when I lock the machine, I can still use the finger print reader to unlock it, but the prompt to scan my finger is not there.  In other cases, like using a sudo command in the command prompt, it is.

Bob
Bonobo Extreme (bonx6)

---

