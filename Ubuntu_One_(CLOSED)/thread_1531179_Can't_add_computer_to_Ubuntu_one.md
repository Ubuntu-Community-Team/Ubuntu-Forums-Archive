---
title: "Can't add computer to Ubuntu one"
date: 2010-07-14
forum: Ubuntu One (CLOSED)
---

### Post by Will130278 on 2010-07-14
Hi

I am running lucid 10.04. I have just run the update manager and updated everything.

I registered for the free 2Gb account on ubuntu one, but I can't add my computer.

The installation guide says a web browser will open when I select the ubuntu one option from the name menu on the desktop. It doesn't.

I read the FAQ page which reports a problem like this.

The solution is apparently to open terminal and type a line which kills the syncdaemon: u1sdtool -q; killall ubuntuone-login; u1sdtool -c.  The daemon stops successfully. The browser is now supposed to open.

Instead, nothing happens for about a minute, then I get an error message saying Errno2 socket error -  name or service not known.

Anyone know how to get out of this one?

---

### Post by Will130278 on 2010-07-15
Ok, I've solved this one myself.

I did the above, then selected the ubuntu one option from the "name" menu and it worked....

---

### Post by duanedesign on 2010-07-16
Thanks for updating the thread with your solution.

---

### Post by Lantau on 2010-07-16
I have a similar problem but the cmd line input described doesn't work. When I select the Me menu item Ubuntu One... I get the Ubuntu One Preferences box with the Name/E-mail/Current Plan listed as Unknown. I've tried various options of being logged into Single Sign On or not but the result is the same. I can get to my dashboard and would have thought it would make sense to have an "add computer" there. 


Have I missed something? When I login via the SSO I get to the Your Account page and appear to be logged in, i.e. there is a log out prompt. But there are NO links to go anywhere else. Almost is if there is no point to logging in. Not very intuitive.

---

### Post by Will130278 on 2010-07-16
Well what I did was open terminal and enter this line:

u1sdtool -q; killall ubuntuone-login; u1sdtool -c

I can't remember if I logged on as a super user first.

try opening terminal and doing this:-

sudo -i

then enter your password..

u1sdtool -q; killall ubuntuone-login; u1sdtool -c

I then got a message saying the syncdaemon had stopped, but no browser. 

dont touch anything for a minute and you should get some weird error message. clear this, then try selecting the ubuntu one option from your name menu. 

When I did this the browswer opened with the add computer option.

---

### Post by Lantau on 2010-07-17
Thanks for taking the time to reply. I was able to make a little progress but still no 'add computer' page. 
Previously I didn't get the error message but entering the '..kill all..' line at a root terminal did trigger the "ubuntuone-syncdaemon stopped." message followed shortly after by a dbus.exception error. A quick qestion, you say 'clear the error' almost implying it was not in the terminal. In my case the error appeared in the terminal but left me at the root@... prompt, i.e. no need to clear. Did I misunderstand something?
However, the original problem remains, when I select Ubuntu One from the me menu I get the Ubuntu One Properties dialog with a disconnected status. Under the devices tab it lists <LOCAL MACHINE> with Connect and Restart buttons. <LOCAL MACHINE> is obviously not the name of my machine and the buttons appear to do nothing. 
My next step is to try with my laptop.
Thanks for your time and I'm open to any other suggestions. 

Lantau.

P.S. Wouldn't it make sense to have an add computer on the dashboard?

---

### Post by Lantau on 2010-07-17
Worked fine on my laptop also running lucid. Didn't even have to stop the ubuntuone-syncdaemon. There's obviously something confused on my desktop, ..any ideas?

---

### Post by duanedesign on 2010-07-18
Are you using Firefox as your default browser?

Make sure Firefox is selected under:
System > Preferences > Preferred Applications

Also are you using any Script blocking software like NoScript?

Another thing, try this command in a terminal and see if it opens a broser to google:

```
xdg-open [http://www.google.com](http://www.google.com)
```

Lastly there might be a left over token or something keeping the process from executing correctly. Follow these instructions to make sure that is not the case.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

---

### Post by Will130278 on 2010-07-18
> **Lantau said:**
> Thanks for taking the time to reply. I was able to make a little progress but still no 'add computer' page. 
Previously I didn't get the error message but entering the '..kill all..' line at a root terminal did trigger the "ubuntuone-syncdaemon stopped." message followed shortly after by a dbus.exception error. A quick qestion, you say 'clear the error' almost implying it was not in the terminal. In my case the error appeared in the terminal but left me at the root@... prompt, i.e. no need to clear. Did I misunderstand something?
However, the original problem remains, when I select Ubuntu One from the me menu I get the Ubuntu One Properties dialog with a disconnected status. Under the devices tab it lists <LOCAL MACHINE> with Connect and Restart buttons. <LOCAL MACHINE> is obviously not the name of my machine and the buttons appear to do nothing. 
My next step is to try with my laptop.
Thanks for your time and I'm open to any other suggestions. 

Lantau.

P.S. Wouldn't it make sense to have an add computer on the dashboard?


Yes, on my machine the error wasn't in the terminal, but came about 1 minute later in a dialogue box outside. 

hmm...this must be more complex than it appears - I wonder if anyone else can help you here?

I agree that it seems a strange way of doing things. I was surprised that there was no option to add the computer in the dashboard.

---

### Post by Will130278 on 2010-07-18
This is the FAQ page I took the solution from:-
[https://wiki.ubuntu.com/UbuntuOne/FAQ#How](https://wiki.ubuntu.com/UbuntuOne/FAQ#How) do I add my computer?

---

### Post by Lantau on 2010-07-19
Thanks everyone it's now working. I suspect it was the default browser suggestion. I started working through duanedesign's suggestions and although I thought firefox was the default I found the default browser was set to "custom". This plus shutting down the ubuntuone daemon opened the web page. 

The spirit of open source is alive and well, thanks!

---

### Post by Krekama on 2010-07-25
> **Will130278 said:**
> 
I am running lucid 10.04. I have just run the update manager and updated everything.
I registered for the free 2Gb account on ubuntu one, but I can't add my computer.

The solution is apparently to open terminal and type a line which kills the syncdaemon: 

u1sdtool -q; killall ubuntuone-login; u1sdtool -c

The daemon stops successfully. The browser is now supposed to open.


This worked for me!  I think what the problem was is that i tried to sync w/ ubuntu1 before i had my SSO created then it just hung there.  that one command killed it, brought it up and i was able to add my computer to begin sync.

---

### Post by Krekama on 2010-07-25
Okay... i take that back.  That allowed me to add my computer.. and it says syncs complete, but nothing gets uploaded, i've selected a folder to sync also.  meh.. i'll reboot, go have a smoke and see if it helps :P

---

### Post by Krekama on 2010-07-25
weee okay.. it's working now! [http://wowignore.com/ubuntu/UbuntuOne.jpg](http://wowignore.com/ubuntu/UbuntuOne.jpg)

---

### Post by duanedesign on 2010-07-25
Looks good!

When in doubt, step out and have smoke 	:wink:

---

### Post by melodram on 2010-08-07
thankyou!

it worked after i deleted the password (key) for ubuntu one!



> **duanedesign said:**
> Are you using Firefox as your default browser?

Make sure Firefox is selected under:
System > Preferences > Preferred Applications

Also are you using any Script blocking software like NoScript?

Another thing, try this command in a terminal and see if it opens a broser to google:

```
xdg-open [http://www.google.com](http://www.google.com)
```Lastly there might be a left over token or something keeping the process from executing correctly. Follow these instructions to make sure that is not the case.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

---

### Post by ellis rowell on 2010-08-07
I've been on Ubuntu One for sometime now and I can't remember having any problems (v10.04). My desktop just seemed to work when set-up and I later added my laptop and synchronised it.

The only problem I found was that I thought that a windows applictaion I use in Wine would need all the files uploaded to work. But No! it only needed the data file and it updates on each computer. I found that any.exe file is set as "read only" so will not work.

---

### Post by krupintupple on 2010-08-15
> **duanedesign said:**
> Are you using Firefox as your default browser?

Make sure Firefox is selected under:
System > Preferences > Preferred Applications

Also are you using any Script blocking software like NoScript?

Another thing, try this command in a terminal and see if it opens a broser to google:

```
xdg-open [http://www.google.com](http://www.google.com)
```

Lastly there might be a left over token or something keeping the process from executing correctly. Follow these instructions to make sure that is not the case.

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Applications->Internet->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

FANTASTIC! this completely and fully repaired a similar issue. excellent stuff!

---

### Post by zeroandone on 2010-08-17
I don't quite understand why it is hard to connect to Ubuntu One. I just installed 10.04 on a desktop, then clicked Me menu and chose Ubuntu One, and I saw Ubuntu One Preference screen, but no web browser was launched. Then an error message came up saying authorization error.

BTW, as an end user, I would love to be able to type in my account credentials instead of seeing the authorization error message with only a "Close" button, when the authorization is failed.

---

