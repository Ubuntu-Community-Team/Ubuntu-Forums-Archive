---
title: "Are updates done over HTTP?"
date: 2012-06-16
forum: Security
---

### Post by Hungry Man on 2012-06-16
> Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US

Just a few but they all seem to be done over HTTP.

I don't know the details of Ubuntu's installation process. Could someone explain why this is and maybe give insight into the process?

---

### Post by Ms. Daisy on 2012-06-16
Well update manager uses port 80 to communicate updates.  It's got to use some port over TCP/IP to communicate.  

What concerns you about it?

---

### Post by haqking on 2012-06-16
> **Hungry Man said:**
> Just a few but they all seem to be done over HTTP.

I don't know the details of Ubuntu's installation process. Could someone explain why this is and maybe give insight into the process?

You can use rsh, ssh, ftp etc

Look in the sources man page at the URI specification

[http://manpages.debian.net/cgi-bin/man.cgi?query=sources.list&sektion=5&apropos=0&manpath=Debian+Sid&locale=en](http://manpages.debian.net/cgi-bin/man.cgi?query=sources.list&sektion=5&apropos=0&manpath=Debian+Sid&locale=en)

and the apt.conf man page

[http://manpages.debian.net/cgi-bin/man.cgi?query=apt.conf&sektion=5&apropos=0&manpath=Debian+6.0+squeeze&locale=](http://manpages.debian.net/cgi-bin/man.cgi?query=apt.conf&sektion=5&apropos=0&manpath=Debian+6.0+squeeze&locale=)

I cant speak for why it defaults to http or how the ubuntu repos are setup though.

---

### Post by SeijiSensei on 2012-06-16
> **Ms. Daisy said:**
> What concerns you about it?

I wondered about that, too.  Are you suggesting it's somehow insecure to use HTTP instead of HTTPS to install packages?  All you're doing is downloading a binary.  Why would it need to be encrypted?

---

### Post by zombifier25 on 2012-06-17
'sides, the packages are digitally signed.

---

### Post by Hungry Man on 2012-06-17
Can you tell me more about the digital signing? 

> I wondered about that, too. Are you suggesting it's somehow insecure to use HTTP instead of HTTPS to install packages? All you're doing is downloading a binary. Why would it need to be encrypted?
When you download a page all you're doing is downloading an .html file. HTTPS provides authentication and validation. I can know that no one has seen or tampered with the file coming to my system.

Were there no signing system and it used HTTP the binary could be replaced in transit and that should obviously raise a few concerns. I knew there was a signing system so I wasn't concerned, just curious.

If I can use HTTPS I'd prefer to. But I'm curious to hear more about the signing process.

---

### Post by SeijiSensei on 2012-06-17
> **Hungry Man said:**
> Were there no signing system and it used HTTP the binary could be replaced in transit and that should obviously raise a few concerns.

Well it doesn't concern me particularly.  I often wonder who these malevolent third parties are who are monitoring my downloads and are so eager to intercept a file in transit. 

There are lots of potential security problems that could happen in theory.  For the vast majority of us the actual danger is functionally zero.

And, as has been pointed out, [signing]("http://en.wikipedia.org/wiki/Digital_signature") insures that the binary I receive is identical to the one being shipped.  PPAs are a concern since most of us just accept the signer's public key with something like add-apt-repository and install the package.  For software from the official repositories I don't think it's much of an issue.

---

### Post by Hungry Man on 2012-06-17
I'm not expecting to be attacked. I don't think there is someone out there who is willing to attack this particular system, which is already fairly strong. It just seems like using HTTPS would be a best practice type thing.

I know what signing is I just don't know the process for Linux. If they all have their own keys that's interesting/ pretty cool. I just don't like to rely on any single system.

---

### Post by SparTacux on 2012-06-17
> **SeijiSensei said:**
> Well it doesn't concern me particularly.  I often wonder who these malevolent third parties are who are monitoring my downloads and are so eager to intercept a file in transit. 


Well - I'm also curious what several billion dollars of cyber weaponry capability buys the Government. Use your imagination - it's probably better than what you can imagine.

Now consider the case that there are always bent judges, bent policemen, and dare I say it bent government cyber security guys. That scenario is quite possible. I wonder how most Ubuntu users would fair if this sort of system ever got aimed in their direction. I'd be curious if even the best of the security Guru's on this site could keep them out.

---

### Post by haqking on 2012-06-17
> **SparTacux said:**
> Well - I'm also curious what several billion dollars of cyber weaponry capability buys the Government. Use your imagination - it's probably better than what you can imagine.

Now consider the case that there are always bent judges, bent policemen, and dare I say it bent government cyber security guys. That scenario is quite possible. I wonder how most Ubuntu users would fair if this sort of system ever got aimed in their direction. I'd be curious if even the best of the security Guru's on this site could keep them out.

I keep a cupboard full of bacofoil, and fashion a fresh hat every 2 to 3 days.

---

### Post by SparTacux on 2012-06-18
> **haqking said:**
> I keep a cupboard full of bacofoil, and fashion a fresh hat every 2 to 3 days.

Yeah me too - the really thick foil. :-)

Apparently, there are many undercover operations on Forums across the internet. There's probably one or two guys in disguise on this forum. I reckon I could sniff them out with my JEDI powers ;-)

I doubt if all of these guys work within ETHICAL boundaries of their job descriptiion. I wouldn't want to upset one by accident. They'd probably want to teach you a lesson you won't forget. Does one need police warranties to ATTACK a target in another country and would such a person be protected by law from cross border operations.

---

### Post by Ms. Daisy on 2012-06-18
> **haqking said:**
> I keep a cupboard full of bacofoil, and fashion a fresh hat every 2 to 3 days. Best. Response. Ever.

---

### Post by dodo3773 on 2012-06-18
Seems like it would make more sense to exploit the packages server side to root as many boxen as possible. So when you download your packages over https you will have an encrypted already exploited package ready to back door you hahaha. Unless you are worried about your own lan I wouldn't worry about it too much. If it is a high high concern for your operation just go source based and inspect the code yourself.

---

### Post by SparTacux on 2012-06-18
> **Ms. Daisy said:**
> Best. Response. Ever.

Now Miss Daisy is probably a fine example of an undercover secret Russian spy using her female wiles to get secrets out of us. The honey trap always works. Many a British MP has fallen for a Russian babe only to discover her links to the KGB. ;-)

---

### Post by Ms. Daisy on 2012-06-18
> **spartacux said:**
> now miss daisy is probably a fine example of an undercover secret russian spy using her female wiles to get secrets out of us. The honey trap always works. Many a british mp has fallen for a russian babe only to discover her links to the kgb. ;-) &#1044;&#1072;, &#1087;&#1088;&#1072;&#1074;&#1076;&#1072;.

---

### Post by Cheesemill on 2012-06-18
> **dodo3773 said:**
> Seems like it would make more sense to exploit the packages server side to root as many boxen as possible. So when you download your packages over https you will have an encrypted already exploited package ready to back door you hahaha. Unless you are worried about your own lan I wouldn't worry about it too much. If it is a high high concern for your operation just go source based and inspect the code yourself.
This is why the packages are digitally signed, it ensures that the package was created by a trusted author.

---

### Post by SparTacux on 2012-06-18
> **Ms. Daisy said:**
> &#1044;&#1072;, &#1087;&#1088;&#1072;&#1074;&#1076;&#1072;.

LOL - You're truly irresistible - I'll tell you anything you vant to know ;-)

As James Bond always said - we've got to keep the British End Up 
You only live twice Ms Daisy - make the most of it :-)

---

### Post by Hungry Man on 2012-06-18
> **dodo3773 said:**
> Seems like it would make more sense to exploit the packages server side to root as many boxen as possible. So when you download your packages over https you will have an encrypted already exploited package ready to back door you hahaha. Unless you are worried about your own lan I wouldn't worry about it too much. If it is a high high concern for your operation just go source based and inspect the code yourself.

I'm not worried. I just feel like it should be kind of... the obvious thing to use a secure method to update or deliver anything like this.

---

### Post by CharlesA on 2012-06-18
It doesn't really matter what delivery method is used cuz the packages are signed with a GPG key.

---

### Post by Hungry Man on 2012-06-18
It's just a matter of relying on one system.

---

### Post by CharlesA on 2012-06-18
I think you can change the protocol used, at least according to here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Hungry Man on 2012-06-18
Using HTTPS breaks at least some of them.

---

### Post by cariboo on 2012-06-19
In order to get a package in the repositories, it must be sponsored by an Ubuntu Developer, see more [here]("https://wiki.ubuntu.com/UbuntuDevelopers").

As far as ppa's go, all someone has to do is sign the Ubuntu Code of Conduct, which needs a digital signature. Once that is done, anything can be uploaded to a ppa. It is then up to you as a user whether you trust that developer or not, you do have the option to check out the source yourself if you have any qualms about downloading it.

---

### Post by zombifier25 on 2012-06-20
And again, I see no reason why you should do this. Not including PPA, Ubuntu's repos are very secure by default.

---

### Post by sauranibh on 2012-06-20
The update performs via HTTP! The source of the update is verified and the file transfered via HTTP. Not https. Coz it would be a waste of security. The files are digitaly signed by the owner for their authentication and Non-repudiation. Also The MAC (Message Authentication Code ) is transfered by the source to check the file intigration.

And also HTTPS is not signing the message, Its the use of SSL or TSL security protocol! There is no need to use any N/W layer security like  SSL for update!

---

### Post by Hungry Man on 2012-06-20
Yeah I knew about the signing before I made the topic. But using HTTPS shouldn't really increase load very much at all and it creates an initial point of failure before one would attack the certificate signing in some kinda MITM attack.

If there were no signing process anyone in the middle could, of course, interfere with the packages. Because of the signing process they would have to do quite a lot to MITM it.

---

### Post by haqking on 2012-06-20
[http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get](http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get)

---

### Post by SeijiSensei on 2012-06-20
> **dodo3773 said:**
> Seems like it would make more sense to exploit the packages server side to root as many boxen as possible.

[Like this, for instance](http://www.theregister.co.uk/2011/01/25/fedora_server_compromised/)

---

### Post by Hungry Man on 2012-06-20
> **haqking said:**
> [http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get](http://askubuntu.com/questions/146108/how-to-use-https-with-apt-get)

Specifying HTTPS breaks updating for me. Nice explanation though, thanks.

I'll figure out which support SSL and which don't at some point. If they aren't all using it it kinda defeats the purpose to an extent.

---

### Post by haqking on 2012-06-20
> **Hungry Man said:**
> Specifying HTTPS breaks updating for me. Nice explanation though, thanks.

I'll figure out which support SSL and which don't at some point. If they aren't all using it it kinda defeats the purpose to an extent.

yeah the server needs to support it obviously, i guess a fair few of the repo servers do not, you could of course do the update through a secure VPN.

---

### Post by Hungry Man on 2012-06-20
True.

---

