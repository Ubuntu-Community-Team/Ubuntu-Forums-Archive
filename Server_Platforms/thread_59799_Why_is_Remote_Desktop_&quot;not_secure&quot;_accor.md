---
title: "Why is Remote Desktop &quot;not secure&quot; according to ubuntuguide.org??"
date: 2005-08-25
forum: Server Platforms
---

### Post by cmh_ubuntu on 2005-08-25
On ubuntuguide.org I noticed that it says Remote Desktop is "not secure":

> Warning! Remote Desktop will only work if there's a GNOME login session
         Leaving computer with an unattended GNOME login session is not secure
         Use (System -> Lock Screen) and off the monitor when computer is left unattended

I want to use Remote Desktop to access my Ubuntu 5.04 machine from a Windows machine.  Both PCs are behind a home firewall/NAT.  

Does the quote above mean that I must log into Ubuntu and stay logged in with my screen unlocked?  I don't see why this would be a problem for many home users, since the machine is physically secured (i.e. inside my locked house)...

Also, I'm assuming the connection between the Ubuntu and Windows machines is not encrypted?  Again, this I could live with since both are behind a firewall?

Is there any other security risk I am missing?

---

### Post by acascianelli on 2005-08-25
Remote Desktop in Ubuntu is just VNC.  Do a google search on VNC security.

---

### Post by duffman25 on 2005-08-25
[QUOTE=cmh_ubuntu]On ubuntuguide.org I noticed that it says Remote Desktop is "not secure":



I want to use Remote Desktop to access my Ubuntu 5.04 machine from a Windows machine.  Both PCs are behind a home firewall/NAT.  

Does the quote above mean that I must log into Ubuntu and stay logged in with my screen unlocked?  I don't see why this would be a problem for many home users, since the machine is physically secured (i.e. inside my locked house)...

Also, I'm assuming the connection between the Ubuntu and Windows machines is not encrypted?  Again, this I could live with since both are behind a firewall?

Is there any other security risk I am missing?[/QUOTE]

I think the guide referes to the fact that the remote desktop gnome provides is just vnc, and in fact, if you try it at home with another computer, you'll see that you can access with the terminal server client a gnome session running without being asked for a password. That's why He states that you should lock your session. Because if you don't do it, anybody could vnc to your machine.

I don't know if gnome's vnc server uses encryption

---

### Post by acascianelli on 2005-08-25
You can set it so that it requires a password when you try to remote in.

---

### Post by cmh_ubuntu on 2005-08-25
Thanks for the info!  Googling VNC answered more of my questions...

So in my scenario, Remote Desktop/VNC would not introduce any security problems?  That is, using VNC between computers that are all behind a firewall is safe, provided that physical access to both machines and the LAN is secured...?  I'm not trying to guard against malicious users who have physical access to the LAN, but rather malicious users outside the firewall/NAT.

---

### Post by acascianelli on 2005-08-25
Yea, you should be ok.  As long as you don't have the VNC port forwarded or the box is on a DMZ.

---

### Post by ekravche on 2005-08-30
What if I deactivated remote desktop? could vnc be started remotely? I hope not. I wouldn't want someone to access my ubuntu machine. I am behind a hardware firewall however. Also when I run ps -e | grep vnc I do not find any processes that match this string. I think I'm safe for now.

---

### Post by cmh_ubuntu on 2005-09-08
[QUOTE=ekravche]What if I deactivated remote desktop? could vnc be started remotely? I hope not. I wouldn't want someone to access my ubuntu machine. I am behind a hardware firewall however. Also when I run ps -e | grep vnc I do not find any processes that match this string. I think I'm safe for now.[/QUOTE]

I'm pretty sure the only way to start the service is if you have control of the machine (e.g. if you already were in using vnc, telnet, secure shell or some other remote way of controlling the system).  So, if vnc/remote desktop is not started you should be ok (at least with that issue).

---

### Post by jdong on 2005-09-10
1) If you have it turned on without a password, it's kinda obvious why it isn't too secure ;)

2) If you have it with a password, the problem is eavesdropping. GNOME's VNC doesn't wrap itself via SSH -- it's just VNC over TCP. People with packet sniffers will be able to see your screen, along with all your keyboard input.

Now, whether that's really an issue... If you have two computers behind a hard-wired router and are using remote desktop at your house, go ahead... it's sort of a physical impossibility for someone else to eavesdrop :).

If you have a wireless network, or if you're VNC'ing over the internet, I don't recommend it. Use FreeNX or open up an SSH session with port forwarding and redirect your VNC traffic through there.

---

### Post by louisgag on 2006-05-02
Yesterday I came home to see that my machine was being run by another user! Although I had a somewhat easy to guess password:  wm12uv    I think the hacker simply bypassed it (Unless it was ip snoofing, but I doubt, you will see why in 2 sec.)

Fortunately, my screen was also looked, with another password and the password box was being hammered by the hacker which tells me the hacker hadn't snooped my screensaver password...

So I wouldn't recommend remote desktop for anyone with the vnc port open on their router.

BTW, I run Ubuntu 5.10 with all those security updates..

Louis

---

### Post by jdong on 2006-05-02
Don't forget that when typing in your password via VNC without SSH, it is sent in plaintext, which means anyone in between or on the same LAN as you on either end can easily see your password with a easy-to-use sniffer like ethereal or ettercap.


Wrap VNC over SSH _ALWAYS_, or use freenx which uses SSH internally anyway. SSH passwords are also harder to brute force because of the 5-second wrong password delay :)

---

### Post by RavenOfOdin on 2006-05-05
I wouldn't use "remote" anything. 

But that's just me.

---

### Post by LordHunter317 on 2006-05-05
[QUOTE=RavenOfOdin]I wouldn't use "remote" anything. 

But that's just me.[/QUOTE]Unfortunately I can think of a million professional scenarios where that kind of view is just not viable.  One involving life safety and costs issues where requiring physical access would cost on the order of five figures every time you wanted access to the box, if not more.  This view isn't a good one to take.  I have yet to possess a job where remote access wasn't useful.

Everybody here has said the right things.  Wrap it in SSH, which is perfectly secure.  This is one of the things SSH was designed for.

Personally, I'm in the "use FreeNX" camp, but that ultimately doesn't matter w.r.t. security.

---

### Post by sphinx on 2006-05-06
[QUOTE=LordHunter317]Unfortunately I can think of a million professional scenarios where that kind of view is just not viable.[/QUOTE]

Thats great, I can think of a million situations where it is viable. Also including life saftey and other niche situations that sound impressive and important to support my opinion. 

Its very quick and easy to secure something by just turning it off, you have no research to do and a guarentee that you wont be exploited though it.

Of course, if you need a service, or even want a service, then this quick and easy option is probably no longer for you.

You absolutly have a point LordHunter317, but lets lay off the grandstanding, eh?

---

### Post by LordHunter317 on 2006-05-06
[QUOTE=sphinx]Thats great, I can think of a million situations where it is viable.[/quote]Wonderful.  That's great.  The point was, saying "I try to avoid it" is basically nonsense.  It's not clear from the OP that a different solution is warranted.  We don't know.  It would be presumptious to say, "Try to avoid this" without more details, which was my point.

 > Also including life saftey and other niche situations that sound impressive and important to support my opinion. Well it's true.  The point to take home is the correct solution is implementation dependent.  If it will cost you say, $50K to have physical access to a machine, you use remote access wherever possible.  That's all.  There are scenarios where physical access simply isn't viable, or where remote access is more convinent even where physical access is viable

> Its very quick and easy to secure something by just turning it off, you have no research to do and a guarentee that you wont be exploited though it.Yes, but you give up the functionality, which is a huge cost to pay. 

> You absolutly have a point LordHunter317, but lets lay off the grandstanding, eh?If I were grandstanding, I'd give actual details and numbers.

---

### Post by sphinx on 2006-05-06
[QUOTE=LordHunter317]"I try to avoid it" is basically nonsense.[/QUOTE]
RavenOfOdin mearly threw that out as an option. It may not suit cmh_ubuntu's situation but its not nonsense because, as you so nicly put it...
[QUOTE=LordHunter317]We don't know. [/QUOTE]

My point is cmh_ubuntu has the option of securing the remote desktop using all the advice given here, or to simply turn it off. Neither of us can make the choice on cmh_ubuntu's behalf, only offer options and advice. So to say that turning it off is not viable, or that "*this view isn't a good one to take*" is a little presumptious. Given that "*We don't know.*"

[QUOTE=LordHunter317]If I were grandstanding, I'd give actual details and numbers.[/QUOTE] Now we're talking a matter of degree.

---

### Post by LordHunter317 on 2006-05-06
[QUOTE=sphinx]RavenOfOdin mearly threw that out as an option.[/quote]No, I would not personally call that post throwing out options and even if it were, my point is that the post was rather inappropriate.  It wasn't helpful in any way, shape, or form.  To me at least, it's patently apparent that simply physically going to the Ubuntu box isn't an option.

Generally, people don't bother with remote access in the first place unless they have need for it.  From that, it follows that telling them, "Don't use remote access" isn't a viable answer unless you have evidence otherwise.

>  So to say that turning it off is not viable, or that "*this view isn't a good one to take*" is a little presumptious. Given that "*We don't know.*"See above.  It's not rational to use remote access software without a reason.

---

### Post by sphinx on 2006-05-06
Well, since we've moved off on a tangent to the original post in debating the validity of an option I'll leave it there.

We've both made our points, and while I dont agree, to take this any further will inevitably involve repeating ourselves, or going down the is-not is-too path.

We'll have to agree to disagree on this one.

---

### Post by mor on 2006-05-13
How can you make a program require sudo to access it? I don't like the fact that anyone using my computer for a few minutes could set up Remote Desktop without being prompted for a password. Also, how do I wrap vnc with ssh? Thanks!

---

### Post by webjabber on 2006-05-26
It is good news. GoToServers offers an unique service on the internet. It makes access servers/computers more secure. You also can host your website at your home. Take a look at [http://www.gotoservers.com](http://www.gotoservers.com)

---

