---
title: "Evolution email client setup"
date: 2005-02-23
forum: The Cafe
---

### Post by Rhizome21 on 2005-02-23
Can anyone help me set up the evolution email client for gmail. I don't quite understand it.

It doesn't ask for port numbers and stuff :S

AIM: Deathaltar47


Thank you :)

---

### Post by Ironi on 2005-02-23
You shouldn't need to supply a port number. Just set it up under 'Receiving Email' like so...

Server Type: POP
Host: pop.gmail.com
Username: [email]yourname@gmail.com[/email]
Use Secure Connection: Always

---

### Post by adbak on 2005-02-23
I don't know how to set up GMail with Evolution, but there is this handy extension for FireFox called GMail Notifier ([http://www.nexgenmedia.net/extensions/](http://www.nexgenmedia.net/extensions/)) that lets you know, via an icon in your status bar, when you have new gmail.

---

### Post by Dylanby on 2005-02-24
You don't need to specify port settings. Just make sure you enable POP in your gmail settings ("Forwarding and POP").

---

### Post by ThePainter on 2005-02-25
Hi,
Yeah I found it easy enough to set up but when I put the secure connection on, it errors saying that it isnt supported ?
I use to use Thunderbird but have changed to Evo cos I think it has a few features that are bettor than Thunderbird.

---

### Post by Dylanby on 2005-02-25
I'm using Evo 2.0.2 (Warty).
For Gmail's receiving/sending settings SSL is set to "Always", "Remember password" is checked & for "Authentication" receiving is "Password" while sending is "Plain".
If your running Hoary you may be experiencing a bug of some sort.

---

### Post by rpjanaka on 2007-06-28
> **Ironi said:**
> You shouldn't need to supply a port number. Just set it up under 'Receiving Email' like so...

Server Type: POP
Host: pop.gmail.com
Username: [email]yourname@gmail.com[/email]
Use Secure Connection: Always


i tried with this, but i was unable to get success, it says "Error while Fetching Mail.

Could not connect to pop.gmail.com: Connection timed out".



i suggest that the reason for this is the proxy settings does not set. because i can connect to our local mail server without any problem
so are there any configuration for change the proxy settings in evolution mail client..?

---

### Post by orange2k on 2007-06-28
I have the same problem with Evolution (with my gmail account): it doesnt even ask me for a password, it simply hangs - "recieving mail" - and nothing happens, so I just use Opera for my e-mail...

---

### Post by ScottJ on 2007-08-04
I suspect we have several versions of Evolution being talked-about on this thread.

My Evolution is v. 2.10.1, and the settings options are different from what's discussed in earlier posts.

Here's how I got Evolution working with gmali.  Using the Account Editor (Edit | Preferences | Mail Accounts):

o  Identity tab: fill in with your full gmail address and name

o  Receiving Email tab: 

[LIST]
[*]Server type: select POP

[*]Server: enter pop.gmail.com

[*]Username: the first part of your email address (e.g., if your email address is "joeschmoe@gmail.com" you'd type "joeschmo" in this field).

[*]Security: in "Use Secure Connection" select "SSL encryption"

[*]Password: You'll probably want to checkmark "Remember password."  There's no place to enter the password; instead Evolution will ask you for it the first time you send/receive.
[/LIST]

o  Sending Email tab:

[LIST]
[*]Server type: select SMTP

[*]Server: enter smtp.gmail.com

[*]Checkmark "Server requires authentication"

[*]Security: Select "SSL encryption"

[*]Authentication: Select "Plain"

[*]Username: See above, first part of your gmail address 

[*]Again, you'll probably want to checkmark "remember password".
[/LIST]


You do not need to set any ports.  They are implied in the connection/encryption types you've specified.

Hope this helps.  It took me a few tries but this works well.  I'm impressed with Evolution.

---

### Post by prachijpp on 2007-11-14
Check this site,

[https://help.ubuntu.com/community/UsingGmailWithEvolution](https://help.ubuntu.com/community/UsingGmailWithEvolution)

It provides you with all the settings that are required. :KS

---

### Post by 50words on 2007-11-14
If you need to set a specific port, it goes after the server. So if your incoming server were mail.example.com, and you needed to use port 1234, you would identify your incoming server as:

```
mail.example.com:1234
```

---

### Post by ecr959 on 2007-11-17
This is for ScottJ

      I was just browsing this thread because I had to re-install everything on my notebook, including the evolution and settings.  I also want to use it for sending gmail ,  I appreciate your clear instructions.  Thanks.

---

