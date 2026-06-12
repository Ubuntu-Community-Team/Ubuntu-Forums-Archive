---
title: "Setting server daemon to run at boot / how to restrict port access to specifc domain?"
date: 2009-07-15
forum: Security
---

### Post by kitcar on 2009-07-15
This question is related to another thread - [http://ubuntuforums.org/showthread.php?t=1213537](http://ubuntuforums.org/showthread.php?t=1213537) - I need to expand on the question though, and therefore believe it to be more appropriate for this forum.

I'm trying to setup an email forwarding server, but am really new to this.

1) I have the server installed (DavMail), but I can only run it as root. I'm thinking this is probably not correct? Who should it be run under, and how to I enable appropriate permissions to enable them to run it?

2) Because I have a dynamic IP, I want to restrict access to the mail forwarding ports by Domain rather than IP. Is this possible? How do I go about doing this?

3) I want to run the server on startup automatically. What's the best method to do this, ensuring it runs under the correct user privileges?

Thanks for all the help!

---

### Post by munky99999 on 2009-07-15
> 1) I have the server installed (DavMail), but I can only run it as root. I'm thinking this is probably not correct? Who should it be run under, and how to I enable appropriate permissions to enable them to run it?
Doesnt sound right. Dont know though. Honestly I probably wouldnt go with davmail.

I do believe postfix does this job.

[https://help.ubuntu.com/9.04/serverguide/C/email-services.html](https://help.ubuntu.com/9.04/serverguide/C/email-services.html)

> ) Because I have a dynamic IP, I want to restrict access to the mail forwarding ports by Domain rather than IP. Is this possible? How do I go about doing this?

Dynamically external? or dynamic internal? If internal. Just reserve dhcp the ip. If external. You might actually have troubles running a mail service at all. Most ISPs in my exerience block such issues.

As for the issue. The issue is still an IP issue. You would simply use dynamic dns services to give yourself a domain name.

> 3) I want to run the server on startup automatically. What's the best method to do this, ensuring it runs under the correct user privileges?
If using the postfix and such method. You shouldnt have to worry about it.

Worst case scenario. [Run scripts in linux.]("http://linux.com/news/enterprise/systems-management/8116-an-introduction-to-services-runlevels-and-rcd-scripts")

---

### Post by kitcar on 2009-07-15
The reason I can't use Postfix is I am not forwarding a POP/IMAP server, but a Microsoft Outlook Web Access account (OWA). Postscript does not support OWA.

I have dynamic external, and use DynDNS to assign a ("somewhat static") domain to my machine. Hence the restricting by domain versus IP.

I know... pretty strange setup!

---

### Post by Rob_H on 2009-07-15
> **kitcar said:**
> 2) Because I have a dynamic IP, I want to restrict access to the mail forwarding ports by Domain rather than IP. Is this possible? How do I go about doing this?


Rather than restricting by domain, which requires reverse-name lookups, it may be more efficient and robust to restrict it by subnet. For example, you could allow connections only from machines with IP addresses like 192.168.x.y. This can be configured via the Uncomplicated Firewall (ufw) tool in Ubuntu. See the **ufw** man page for details. There's also a GUI you can install called **gufw**, although I haven't used that.

> **kitcar said:**
> 
3) I want to run the server on startup automatically. What's the best method to do this, ensuring it runs under the correct user privileges?

Most servers that are designed to run in the background as a daemon come packaged with a startup/shutdown script that gets installed to the **/etc/init.d** directory. If DavMail comes with such a script, you can configure it to start at boot and stop at shutdown using the **update-rc.d** tool in Ubuntu. Again, see the man page for usage. If DavMail doesn't come with an init script, you can write one yourself, but at that point, I'd be looking at an alternatives like Postfix, which work quite well on Ubuntu.

---

### Post by kitcar on 2009-07-17
I guess our posts were close enough together that you didn't see my reply - unfortunately I need to use DavMail, as I am trying to sync with Outlook Web Access.

OK, let me simplify the question: when I run DavMail as root, it works fine. When I run it as a user, It can't bind to any ports. How do I give a user the ability to run a server daemon and bind to a port?

Thanks

---

### Post by Rob_H on 2009-07-17
> **kitcar said:**
> I guess our posts were close enough together that you didn't see my reply - unfortunately I need to use DavMail, as I am trying to sync with Outlook Web Access.

OK, let me simplify the question: when I run DavMail as root, it works fine. When I run it as a user, It can't bind to any ports. How do I give a user the ability to run a server daemon and bind to a port?

Thanks

Yes, I think our replies crossed each other on the wire. 

I don't believe it is possible for a non-root user to bind to ports below 1024. Can you configure it to use a higher port number? You might also want to look at [xinetd]("http://xinetd.org/"), which offers access control and other "wrapper" features for daemons. I'm still not entirely clear on how you have things set up, so if you're still stuck, please explain in more detail about what the moving parts are and who's connecting to whom. Good luck.

---

### Post by kitcar on 2009-07-17
Interesting - 
I'll explain the whole story in order to make sure we're all on the same page:

I work remotely quite often. My work email account is only accessible via Microsoft Exchange server. Because of this, when outside of the office I can only access my work email via Outlook Web Access (OWA) - which is quite frustrating as a number of essential features only work if you use Internet Explorer.

In my search for a method to access the OWA account via Thunderbird or a similar app, I discovered DavMail - it "wraps" Outlook Web Access into SMTP, IMAP, POP, and CalDav - tested it as root locally, works great!

So now the two issues I am trying to solve are:
1) How to set DavMail up as a user other than root
2) How to restrict access to the ports DavMail runs

The second point isn't as crucial as the first - basically what I was thinking was that if DavMail is running at my home always, and I expose the open ports via my router, than when I am away from on my 3G card I can still use my home DavMail installation. I thought leaving the port open to the world could be a slight risk, so limiting to just the domain of my 3G provider would at least block out the majority of baddies. 

Hopefully this explanation helps more :)

---

### Post by Rob_H on 2009-07-17
Hmm... DavMail sounds pretty interesting. I might have to look at that myself. Anyway, my previous recommendations still stand. Either see if you can configure it to use a higher port or see if it'll play with **xinetd**, which could potentially address both of your concerns.

Another option--albeit more heavyweight--would be to isolate your DavMail installation inside a virtual machine (VirtualBox, VMWare, Xen, KVM, etc.). That way, it can run as root and still be sandboxed quite effectively from the host OS. If you run a minimal Linux install and DavMail, the footprint would probably be relatively small.

---

### Post by Rob_H on 2009-07-17
Yet another option would be SSH port forwarding, which has the added benefit of encryption. There's a very good tutorial om setting that up [here]("http://magazine.redhat.com/2007/11/06/ssh-port-forwarding/").

---

### Post by kitcar on 2009-07-18
SSH port forwarding sounds interesting - I will investigate further, thanks!

---

### Post by Rob_H on 2009-07-18
> **kitcar said:**
> SSH port forwarding sounds interesting - I will investigate further, thanks!

Yes, it's quite cool. Kind of like an ad hoc VPN.

---

### Post by Rob_H on 2009-07-20
I've done some reading on DavMail and I'm curious as to why you want to run it on a separate server. Since it's basically just acting as a stateless bridge to MS Exchange, wouldn't it be easier and faster to just run it on the same box as your mail client?

---

### Post by kitcar on 2009-07-22
Great Question! The answer is mobile email clients :) Can't run DavMail on my phone unfortunately! 

FYI - I've got it setup now, although I need to make it more secure... Basically I used IPTables to internally forward 110 and 25 to high port numbers which not root users can bind to. I am then running DavMail (via nohup) as a regular user on those higher ports.

At least by preventing DavMail from running as Root I (hope) to have avoided the biggest security issues. The next (minimum) steps I am considering is using IPTables to restrict access to a few blocks (i.e - the one my cell phone 'net access uses, etc...) 

Unfortunately I don't believe DavMail supports secure POP3 / SMTP, so I still have the issue of transmitting username and passwords over plain text.

---

### Post by Rob_H on 2009-07-22
I see. I guess SSH tunneling from your phone isn't an option either.

---

### Post by kitcar on 2009-07-22
exactly
Good news though is the beta version of DavMail appears to support SSL ( [http://sourceforge.net/forum/forum.php?forum_id=964200](http://sourceforge.net/forum/forum.php?forum_id=964200) ) - just need to figure out how to implement it...

---

