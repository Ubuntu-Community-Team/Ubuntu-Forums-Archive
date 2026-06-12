---
title: "Sendmail Help"
date: 2007-12-12
forum: Server Platforms
---

### Post by kmac on 2007-12-12
Set up sendmail and can send email no problem to anyone. However, I'm having trouble receiving it. I have port 25 forwarded and i can receive email from other users on the machine, but cannot receive from say, [email]emailguy@yahoo.com[/email].

i think i installed everything ok but any help would be nice. i'm new to this program but i've done my homework and just think i might have missed something.

any help would be appreciated

thanks,

--Kyle

---

### Post by HermanAB on 2007-12-13
Hmm, good luck with Sendmail...

Check your DNS settings.  A mail server needs both MX and PTR records.

Cheers,

Herman

---

### Post by infinitezero on 2007-12-13
Kmac,
Depending on your ISP most will block port 25, so people will not setup a server on a home user account. You might what to change your SMTP listening port to something other than 25.


iz

---

### Post by kmac on 2007-12-13
i've got mx and ptr records but how do i check if port 25 is open?

---

### Post by HermanAB on 2007-12-13
Test connectivity with telnet:

$ telnet your.public.ip.address 25

You should get the server banner.

You can test any TCP port like that, for example Samba (Windows):
$ telnet win.dows.ip.address 445

That should give the Samba banner.

Cheers,

H.

---

### Post by kmac on 2007-12-13
yeah i checked that the port is blocked (should have figured). i know it's isp cus i have forwarding on the router. However, can i have smtp listen on a different port?

--Kyle

---

### Post by kmac on 2007-12-13
or better yet how would i configure to use my isp's smtp server?

--Kyle

---

### Post by HermanAB on 2007-12-13
Still sendmail?  I doubt that you would get much help anywhere with sendmail.  Postfix and Qmail are the industry standard replacements for Sendmail.

Otherwise, if you don't want to waste any time, see the threads on Citadel and install that.  It only takes about 20 minutes to run the Quick Install script and then you'll have something far superior.

Cheers,

Herman

---

### Post by kmac on 2007-12-15
Alright, I've switched to postfix from sendmail and now I'm completely stuck. I think I have everything configured correctly (maybe not). Regardless... this is going to sound really stupid but... how do I send mail now with postfix? Can I use the "mail" command like I did with sendmail? Also, is this still going to run through port 25 like sendmail did? If so, I'm back to square one and now just a little bit more confused. I've been through maybe 80 tutorials and a book or two and I'm still stuck. 

Any help would be grand.

--Kyle

---

### Post by HermanAB on 2007-12-15
The best postfix tutorials are on the postfix.org web site.

Postfix is a drop in replacement for sendmail and even comes with a script called sendmail that connects to postfix.  You can still send mail with the mail command.  Postfix still runs SMTP on port 25.  The main difference is that the configuration file main.cf is human readable.

---

### Post by kmac on 2007-12-15
so there's no way to just change the port?

--Kyle

---

### Post by HermanAB on 2007-12-16
You can add additional listeners in master.cf.  However, since the whole world sends mail on port 25, it won't help you much.

---

