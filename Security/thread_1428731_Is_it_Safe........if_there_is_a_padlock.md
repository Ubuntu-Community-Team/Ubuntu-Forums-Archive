---
title: "Is it Safe........if there is a padlock"
date: 2010-03-13
forum: Security
---

### Post by He no rat he Basil on 2010-03-13
I notice that on gmail inbox a small padlock is present in the toolbar while viewing and sendin email.  This is not the case for ymail of hotmail.  Equally both of the latter flag that i am leaving an encrypted area when i use them.  Does this mean gmail is automatically encrypted so safer?#-O

---

### Post by amauk on 2010-03-13
The padlock means you are using an encrypted connection to Google's mail server
(HTTPS, as opposed to plain HTTP)

Encrypted connections provide a guarantee that only the sender and recipient can view the contents of a communication.
anyone sitting in the middle (someone else on your network / your ISP / etc.) cannot view the message.

depends what you mean by "safer"
You are protected against [Man in the Middle Attacks](http://en.wikipedia.org/wiki/Man-in-the-middle_attack)

---

### Post by coldraven on 2010-03-13
In the Gmail options you can select "Always use https", I would make sure that you do as it gives more security.
Maybe this is enabled by default now, it was not last year.

---

### Post by OpSecShellshock on 2010-03-13
Yes, gmail by default always uses https. The padlock means, as stated above, that the connection is encrypted. In and of itself, this does not protect you from a man in the middle attack, since you have to be sure that you are connecting directly to the server of the domain you're logging in to, rather than hitting a rogue server that is just passing your credentials along and intercepting the communication in both directions after the authentication has taken place, thus making it readable (this is pretty rare, so don't freak out). This is where certificates come in. A lot of sites that require authentication will provide a certificate to your browser that confirms the identity of their servers. The visual result of this will be a blue or green name that shows up in the left of your browser's address bar.

When looking at a gmail account, every page will be sent over https by default. For other webmail providers, they use https and certificates for the login screen, but the actual page for viewing messages will be unencrypted. That's why the warning comes up to let you know that you're leaving an encrypted page for one that's not. It isn't a huge deal, since it's actually easier to compromise someone's account (and therefore be able to read the messages on the server side) than it is to intercept communication in transit. Just keep your passwords strong and avoid phishing, and for the most part you'll be fine.

---

### Post by MarkC502 on 2010-03-13
Depends on if the icon shows up where it should in Firefox or if it shows up to the left of your URL address. Also you must visually verify that you are on an https: and not an http: server.     

I last week scripted a Ettercap + SSLstrip ARP poison Mitm script as a security demo tool which will Mitm your traffic and uses SSLstrip on my machine to actually log into the SSL site, while the victim will see a lock appear next to their URL and Gmail functions with no other telltales except the missing "s" in htps and the lock being in the wrong location.     

So there are tools out their to strip off your SSL and feed you &quot;the victim&quot; a standard http feed but with the addition of a lock icon, albeit in the wrong location but people just see the lock and think "I'm safe".  I wouldn't use open wifi with secure transactions etc unless you use a VPN tunnel back to your home or office router. That is the best way to use Open communications is to route your comms in a tunnel to somewhere you control via a VPN tunnel.

Note linking directly to the HTTPS address does cause the hacker more trouble and would stop the attack I outlined above, But this is not always possible and https addresses are never the top hits on a google search for any of the top places people go anyway.     

Hope that helps,    

Mark

---

