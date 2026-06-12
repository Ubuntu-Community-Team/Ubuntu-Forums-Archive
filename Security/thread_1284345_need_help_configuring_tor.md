---
title: "need help configuring tor"
date: 2009-10-06
forum: Security
---

### Post by Smiley Coyote on 2009-10-06
At Ubuntu's [help site]("https://help.ubuntu.com/community/TOR") the following is stated:

You will need to add the following repositories to your /etc/apt/sources.list file: 

Ubuntu 8.10 (Intrepid Ibex):

deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) intrepid main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) intrepid main


I don't know where to even find that file.  I am not but a little bit into this instructional and I am already lost.  Truth be told, I already have TOR installed but it has failed to work over and over.  The program has several prompts to help troubleshoot, none of which are making a difference so I thought I would start from the beginning with the above tutorial but am already in a no man's land.

Can anyone direct me to another, more explicit and newbie-oriented set of instructions, or help me themselves?

*

---

### Post by Anarci on 2009-10-06
Rather than attempting to add the repos directly to your sources.list file try going
System -> Administration -> Software Sources 
"Other Software" tab and then click add
Paste the repo address in the input box and click on to add it.

You night be starting to look for the file in the wrong place, open your file browser and click on the computer button to go to your computers root directory, you should be able to find the file from there

---

### Post by Sarmacid on 2009-10-06
```
gksudo gedit /etc/apt/sources.list
```
Paste that into a terminal to edit the the file you need and add those lines to it. I've followed that guide and it's worked out perfectly for me.

---

### Post by Smiley Coyote on 2009-10-07
When opening the graphical user interface for TorK and hitting "play" I get the following:

TorK cannot connect to Tor!
Message: Nothing. TorK tried to connect to Tor and failed.
Reason: If you are trying to manage a remote or already-running instance of Tor you may not have configured the address and/or port of the Tor server correctly.
Would you like to configure the address and port now?


The thing is, when I go to the Tor site that is designed to check to see if I connected using Tor or not, it says I am.  I still can't shake, because of the above, the idea that something is still wrong however.

Little help?

Thanks in advance.

*

---

### Post by Smiley Coyote on 2009-10-08
> **Smiley Coyote said:**
> When opening the graphical user interface for TorK and hitting "play" I get the following:

TorK cannot connect to Tor!
Message: Nothing. TorK tried to connect to Tor and failed.
Reason: If you are trying to manage a remote or already-running instance of Tor you may not have configured the address and/or port of the Tor server correctly.
Would you like to configure the address and port now?


The thing is, when I go to the Tor site that is designed to check to see if I connected using Tor or not, it says I am.  I still can't shake, because of the above, the idea that something is still wrong however.

Little help?

Thanks in advance.

*

I should have stated that I followed the instructions of the first reply and for the first time I got a positive result from [Tor's check site]("https://check.torproject.org/").  So why is the program itself telling me otherwise.  In other words, which kind of malfunction is occuring, the check or the feedback I am getting from the prog itself?

---

### Post by Sarmacid on 2009-10-08
The actual tor wasn't failing, what failed was that program Tork.

```
**TorK** cannot connect to Tor!
Message: Nothing. **TorK** tried to connect to Tor and failed.
```
And in that error message it tells you why
```
Reason: If you are trying to manage a remote or already-running instance of Tor you **may not have configured** the address and/or port of the Tor server correctly.
Would you like to configure the address and port now?
```
It even asks you to configure what was wrong. Read the errors, many times they will tell you what's wrong without the need to look up stuff on the internet.

---

### Post by Smiley Coyote on 2009-10-11
> **Sarmacid said:**
> The actual tor wasn't failing, what failed was that program Tork.

```
**TorK** cannot connect to Tor!
Message: Nothing. **TorK** tried to connect to Tor and failed.
```
And in that error message it tells you why
```
Reason: If you are trying to manage a remote or already-running instance of Tor you **may not have configured** the address and/or port of the Tor server correctly.
Would you like to configure the address and port now?
```
It even asks you to configure what was wrong. Read the errors, many times they will tell you what's wrong without the need to look up stuff on the internet.

Yes but, as I stated, "the program has several prompts to help troubleshoot, none of which are making a difference so I thought I would start from the beginning with the above tutorial but am already in a no man's land."

Now, it keeps telling me to check my Konqueror settings but I am using Firefox and its Tor button to connect.  Is this why I am succeeding with Firefox but still getting an error?  Is the K in TorK the reference to Konqueror?

---

### Post by Smiley Coyote on 2009-10-13
> **Smiley Coyote said:**
> Yes but, as I stated, "the program has several prompts to help troubleshoot, none of which are making a difference so I thought I would start from the beginning with the above tutorial but am already in a no man's land."

Now, it keeps telling me to check my Konqueror settings but I am using Firefox and its Tor button to connect.  Is this why I am succeeding with Firefox but still getting an error?  Is the K in TorK the reference to Konqueror?

Nobody?

---

### Post by ackanao on 2009-10-13
Try stoping Tor and then let the Tork start it for you:

```
sudo /etc/init.d/tor stop
```

If that fails, make sure that the Tor control port is open - just comment it out from the **torrc** file and try again (it's located in "etc/tor").

PS. You're using the wrong repositories - use this one instead:

[http://www.torproject.org/docs/tor-doc-unix.html.en]("http://www.torproject.org/docs/tor-doc-unix.html.en")

---

### Post by Smiley Coyote on 2009-10-14
> **ackanao said:**
> Try stoping Tor and then let the Tork start it for you:

```
sudo /etc/init.d/tor stop
```

If that fails, make sure that the Tor control port is open - just comment it out from the **torrc** file and try again (it's located in "etc/tor").

PS. You're using the wrong repositories - use this one instead:

[http://www.torproject.org/docs/tor-doc-unix.html.en]("http://www.torproject.org/docs/tor-doc-unix.html.en")

I'm afraid I don't know how to comment something out, in, or anywhere else.  I followed the instructions for 'Option One" [here]("http://www.torproject.org/docs/debian.html.en#ubuntu").  This is strange: I got there by clicking on the link you provided but, alas, this is not the link you provided.  Okay, were following the instructions that I did the right way to go?

If so, how do I comment something out of the doc you referenced?

---

### Post by Smiley Coyote on 2009-10-14
> **ackanao said:**
> Try stoping Tor and then let the Tork start it for you:

```
sudo /etc/init.d/tor stop
```

Okay, I stopped Tor with the command line you provided, then used TorK to start it up again and at first I got the same error message I was getting.  When I clicked that I did not want to connect to an already running instance, I got this:

"Message: Traffic on port 80 is not encrypted. Passwords transmitted on this channel could be harvested by the owner of the exit node.
Reason: 
Try to use the secure version of services (e.g. https: instead of http:) if you are entering a username and password or the content is sensitive. Would you like to see an explanation of why using Tor can make un-encrypted traffic potentially less secure than normal?"

As I said earlier, I was already getting the thumbs up from the site set up by Tor Project to check to see if I was properly going through the Tor network and it said yes, as it does now.  I wanted to make sure there were not any security gaps resulting from the error message I was getting.  Now, instead of a green onion icon for Tor in my taskbar, I have an orange one.  I have no idea what this all means.

Will I have to stop Tor and restart it every time or is this a way to lessen my security because of the prompt regarding port 80?

---

### Post by Smiley Coyote on 2009-10-15
TorK has passed an invalid configuration file to Tor!
Message: Oct 15 12:09:10.047 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
This means: Please report this using 'Help->Report Bug' in the menu. Try to provide as much detail as possible. Thanks!

------------------------------------------------------------

Little help?  Tor's site says I am connecting via Tor but I get constant errors.  I would LOVE to know if I can ignore them, given that I seem to be connecting any way or if I am limited because of these errors, or if I really have the security that I am expecting.

---

### Post by ackanao on 2009-10-15
Sorry I made a mistake - I meant what you need to do is to uncomment that line (sorry for my bad english). So, make sure that there's no " # " sign in front of it - it should look like this:

```
ControlPort 9051
```

But it doesn't matter because it looks like your Tor is working OK (I mean that it looks like that Control Port is already open). You need to configure your TorK - I don't use it so I can't help you with that.

> "Message: Traffic on port 80 is not encrypted. Passwords transmitted on this channel could be harvested by the owner of the exit node.
Reason:
Try to use the secure version of services (e.g. https: instead of http if you are entering a username and password or the content is sensitive. Would you like to see an explanation of why using Tor can make un-encrypted traffic potentially less secure than normal?"

About that warning:

I think it's nothing serious; TorK just informs you to use https (SSL) whenever you transfer "sensitive" information through Tor, for example when you pass your Gmail login credentials make sure you use https.

> TorK has passed an invalid configuration file to Tor!
Message: Oct 15 12:09:10.047 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
This means: Please report this using 'Help->Report Bug' in the menu. Try to provide as much detail as possible. Thanks!

Stop Tor and then use TorK to start it.

---

