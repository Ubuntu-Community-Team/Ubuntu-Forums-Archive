---
title: "My website host is blaming users for server virus...?"
date: 2009-07-31
forum: Security
---

### Post by Orographic on 2009-07-31
Hi there,

I'm a bit confused. My website host in Australia is suggesting that the Gumblar virus or a related virus is a clientside problem that is causing problems on their servers. I run Jaunty with all updates and use NoScript as well. I only use software out of the repos and surf very safely. The server I am on with them is a shared hosting server.

Do I need AV software? They suggested maybe this for Ubuntu:

[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)

This is the email from them:


" We wish to make you aware of a client-side virus that has the potential to affect any hosted websites you have with us or any other web host.

As the threat from this virus has been evolving, we have been proactively monitoring our systems and dealing with the threat appropriately. The measures taken to date have been to reset infected customer accounts' passwords, clean infected websites, and proactively monitor for re-infection.

This is a global threat that is affecting hundreds of web hosts, and hundreds of thousands of websites. The virus, a variant of which was originally known as 'Gumblar', searches for FTP credentials stored on a client's computer, logs into the web server using those details, and modifies site files in order to propagate itself to other machines (when the infected site is viewed in a web browser).

With the above in mind, we are recommending all customers perform the following precautionary steps as soon as possible:

- ensure that your anti-virus software is fully up to date and perform a full virus scan.

- employ the use of an anti-malware utility (such as the tool found at [http://malwarebytes.org/mbam.php](http://malwarebytes.org/mbam.php)), which will compliment your anti-virus software and further reduce your exposure to exploits of this nature (note that we are in no way affiliated with this software vendor, and encourage you to conduct your own research to determine if the application is appropriate for your needs).

Once you have performed the above, no further action is required on your part unless we contact you directly.

If we detect that your account has been infected, we will reset your password and clean the infection from your hosting account. We will then notify you of the action taken and request you run the abovementioned scans on your computer once more."

What should I do? I doubt an infection is coming from my machine. I have to other websites with other hosts and they are updated using this same Ubuntu machine and have had no problems at all.

---

### Post by bodhi.zazen on 2009-07-31
Looks like a generic e-mail and the link they gave is for windows.

E-mail them back and point out to them that you use Linux. Ask them to identify they virus for you.

Otherwise, so long as you do not use windows at all, you should be good to go.

---

### Post by Orographic on 2009-07-31
Thanks for that. You see, some weeks ago my website got infected but I am on shared hosting so it seems it wasn't from me but a vulnerability on the shared hosting server.

Most people on this server use Windows to update their sites so the infection could have come from that or a vulnerability on server software.

My site ftp was blocked and my password reset which was annoying as it probably has nothing to do with my system being vulnerable.

Still, I guess that is part of being on shared hosting...

---

### Post by QIII on 2009-07-31
I don't think I'd say "Oh, I run Linux, so I'm OK on this one."

This appears to be hitting Linux Hosting Servers pretty hard.  Googled a bunch of references.

Here's one.

[http://blog.1oasis.net/2009/06/linux-hosting-gumblar-attack.html](http://blog.1oasis.net/2009/06/linux-hosting-gumblar-attack.html)

---

### Post by lisati on 2009-07-31
It sounds like an issue that might be better addressed at the server end, perhaps some vulnerability in the hosting software.

---

### Post by Orographic on 2009-07-31
Yeah, I'm not saying that at all. I'm actually trying to understand what I should do to protect my system? Is it worth installing say, Avast for Linux?

---

### Post by QIII on 2009-07-31
I don't remember where I read it, but I googled something like "Gumblar virus Linux" and one of the hits did talk about how to protect your server.

---

### Post by bodhi.zazen on 2009-07-31
It is a windows attack. It does not infect the server (at least I could not find a report where the server was infected). The compromised windows clients use ftp to upload files to the server.

Once the files are deleted from the server, the server is clean. The hack does not propagate on the server.

The way to protect the server is - delete /var/www (or similar) an restore from backup and do not use ftp.

Many sites say the best way to protect yourself is to avoid using windows and likewise I could not find any report where a Linux client was affected.

---

### Post by Orographic on 2009-07-31
But this is a shared Linux hosting server so if its a Windows attack are you saying that the Windows based machines using ftp are infecting it? How?

How can anyone not use ftp for websites on shared hosting?

---

### Post by bobince on 2009-07-31
> **Orographic said:**
> But this is a shared Linux hosting server so if its a Windows attack are you saying that the Windows based machines using ftp are infecting it?

That would be a possibility, but the way the current attacks are usually doing it is simply by stealing the infected users' passwords. The attacker then logs into FTP from elsewhere* to upload the payload, which is typically SEO spam and iframes to exploit sites like gumblar. (Which themselves would install the original malware that steals the passwords...)

(*: typically this is automated and comes from other compromised machines and proxies)

> How can anyone not use ftp for websites on shared hosting?Use SFTP. FTP has no legitimate use in 2009. Unfortunately many noddy hosting outfits still rely on it.

Although a compromised home machine could also have its SFTP-client passwords stolen, the current attacks aren't doing that, they're sniffing FTP passwords over the wire.

As for anti-virus, it's a complete waste of time for Linux at the moment. As opposed to on Windows, where it's only an almost-complete waste of time. :-) Any machine known to have been hit by browser exploits should simply be reinstalled; you can't rely on anti-virus to clean properly.

---

### Post by bodhi.zazen on 2009-07-31
> **bobince said:**
> That would be a possibility, but the way the current attacks are usually doing it is simply by stealing the infected users' passwords. The attacker then logs into FTP from elsewhere* to upload the payload, which is typically SEO spam and iframes to exploit sites like gumblar. (Which themselves would install the original malware that steals the passwords...).

This seems to be the case, although the script is encrypted and I have not seen a full description as to what it does.

Also the "fix" server side is to change the ftp password, hardly an indication the (linux) host is compromised, it is a (ftp) password compromise.

---

### Post by QIII on 2009-07-31
> **bodhi.zazen said:**
> It is a windows attack. It does not infect the server (at least I could not find a report where the server was infected). The compromised windows clients use ftp to upload files to the server.

I guess I should have been more clear.  You are right.  It is passing through linux hosting servers, not "infecting" them.

Linux systems are just like a biological "carrier" and are themselves asymptomatic.

What I was trying to say is that "I'm running Linux" doesn't mean that this is of no concern.

---

### Post by Orographic on 2009-08-04
Why is it of a concern to those of us running Linux? How can my computer be infected when this virus is a Windows attack? Or are you talking about the servers simply seeing this virus via the Windows ftp details being harvested?

I still can't work out how my website got infected when I am using Ubuntu, how could my ftp details have been harvested?

Or is it just a situation of websites on shared hosting getting cross infected?

---

### Post by bodhi.zazen on 2009-08-05
> **Orographic said:**
> Why is it of a concern to those of us running Linux? How can my computer be infected when this virus is a Windows attack? Or are you talking about the servers simply seeing this virus via the Windows ftp details being harvested?

I still can't work out how my website got infected when I am using Ubuntu, how could my ftp details have been harvested?

Or is it just a situation of websites on shared hosting getting cross infected?

Hard to know without forensics. You should ask your hosting service for more information.

---

### Post by Orographic on 2009-08-05
Yes, have done that. There are quite a few folk that have had websites infected but are either running Linux or Apple machines. Even some of the Windows machines using this host have come up clean after intense scans, so perhaps its an infection that can moved across sites on a shared hosting setup.

---

### Post by bodhi.zazen on 2009-08-05
> **Orographic said:**
> Yes, have done that.

Show us the forensics data then.

[/quote]There are quite a few folk that have had websites infected but are either running Linux or Apple machines. Even some of the Windows machines using this host have come up clean after intense scans, so perhaps its an infection that can moved across sites on a shared hosting setup.[/quote]

Without forensics you would be guessing. From the links I read earlier the problem is with windows machines. Compromised windows machines then send a password to a central server and crackers can then access the server via ftp.

Now it depends on how ftp is set up on the server =) Does the password belong to an administrator ?

You see, without forensics you really do not know.

---

### Post by Orographic on 2009-08-05
Sorry, I meant that I had contacted my host not that I had forensics.

I only have the email below and also this thread on WP:

[http://forums.whirlpool.net.au/forum-replies.cfm?t=1234330&p=4](http://forums.whirlpool.net.au/forum-replies.cfm?t=1234330&p=4)


'We wish to make you aware of a client-side virus that has the potential to affect any hosted websites you have with us or any other web host.

As the threat from this virus has been evolving, we have been proactively monitoring our systems and dealing with the threat appropriately. The measures taken to date have been to reset infected customer accounts' passwords, clean infected websites, and proactively monitor for re-infection.

This is a global threat that is affecting hundreds of web hosts, and hundreds of thousands of websites. The virus, a variant of which was originally known as 'Gumblar', searches for FTP credentials stored on a client's computer, logs into the web server using those details, and modifies site files in order to propagate itself to other machines (when the infected site is viewed in a web browser).

With the above in mind, we are recommending all customers perform the following precautionary steps as soon as possible:

- ensure that your anti-virus software is fully up to date and perform a full virus scan.

- employ the use of an anti-malware utility (such as the tool found at [http://malwarebytes.org/mbam.php](http://malwarebytes.org/mbam.php)), which will compliment your anti-virus software and further reduce your exposure to exploits of this nature (note that we are in no way affiliated with this software vendor, and encourage you to conduct your own research to determine if the application is appropriate for your needs).

Once you have performed the above, no further action is required on your part unless we contact you directly.

If we detect that your account has been infected, we will reset your password and clean the infection from your hosting account. We will then notify you of the action taken and request you run the abovementioned scans on your computer once more.'

---

### Post by bodhi.zazen on 2009-08-05
That is a generic informational message. Nowhere in that message does it say your server was "infected" nor does it say they reset your passwords.

The very last line states :
> If we detect that your account has been infected, we will reset your password and clean the infection from your hosting account. We will then notify you of the action taken and request you run the abovementioned scans on your computer once more.'So:

1. As has been stated in this thread the malware does not affect Ubuntu. So if you run ubuntu you do not need to do anything further.

The malware affects WINDOWS and searches WINDOWS for stored ftp passwords and then uploads the passwords to another 3rd location. The password to your server is then used to upload compromised files to your server. The server itself is not affected and the malware does not propopgate server side.

2. As has been stated in this thread, the malware is not known to propagate on servers.

3. I think we have a failure to communicate. Without forensics , ie an analaysis of the compromise, you really can not know anything further. If your provider will not or is unable to send you any further information that is the end. Any discussion without forensics would be pure conjecture.

---

### Post by hallu on 2009-11-07
> **bodhi.zazen said:**
>  1. As has been stated in this thread the malware does not affect Ubuntu. So if you run ubuntu you do not need to do anything further.
  This gumblar seems to be still spreading. I run ubuntu and one of the sites I visit was infected by this malware. I hope my machine and passwords aren't compromised.

---

### Post by rookcifer on 2009-11-07
OP, has your personal site even been infected?  The e-mail you posted did **not** say that, but, as others have said, it seemed more like a generic e-mail that warned of the potential danger and what to do in the event your site falls victim. 

As for Gumblar, all of the talk I have seen suggests that only Internet Explorer users are affected.  I am assuming you aren't running IE on Ubuntu ;)  The virus enters IE via a flaw in Flash or Adobe Reader and then looks for FTP credentials and uses them to infect another site, and so on.  This would likely require admin/root privileges on both Windoze or Linux.  But since you run Linux, your browser would not have root access (as opposed to most Windoze users who surf with admin privileges leaving their machine wide open to attack).

Bottom line:  I am highly doubtful you have been affected by this.

---

### Post by Jive Turkey on 2009-11-07
Its not unheard of for web hosting companies to either lie or be confused about the point of vulnerability.  They may try to save face by saying its a client side issue when in fact the shared host has been compromised.

---

### Post by bodhi.zazen on 2009-11-07
> **hallu said:**
> This gumblar seems to be still spreading. I run ubuntu and one of the sites I visit was infected by this malware. I hope my machine and passwords aren't compromised.

I have not specifically looked at this issue since August.

Last time I looked the malware ran on Windows clients and uploaded ftp passwords to the server.

The server itself was not compromised.

So:

I suggest you use sftp or scp rather then ftp.

---

