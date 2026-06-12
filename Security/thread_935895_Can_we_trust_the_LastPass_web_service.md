---
title: "Can we trust the LastPass web service?"
date: 2008-10-02
forum: Security
---

### Post by RRFarFar on 2008-10-02
All right, I guess most of you are familiar with the web service called LASTPASS - [https://lastpass.com/](https://lastpass.com/). There is an extension for firefox and it work in linux - [https://addons.mozilla.org/ru/firefox/addon/8542](https://addons.mozilla.org/ru/firefox/addon/8542)

Like in a foxmarks service we can use sync tool to have our passwords across several PCs. Since I am using ubuntu I would like to ask this question here, although it is not related to Ubuntu Linux in a pure sense. The reason why I am posting it here is to ask people of the alternatives and trustworthiness to such services. Can it be trusted??? 
As far as my opinion, this service is very convenient to use, but how are they keeping it alive? Where is the source of their money? Maybe they are using this service for marketing and some other purposes?? Who knows....

When I was under XP, a year ago I as using StickyPassword - [http://www.stickypassword.com/](http://www.stickypassword.com/). A fairly unknown tool which have remarkable integration with FF and IE. Also it had encryption, and all the passwords were located on my PC in an encrypted, password protected database. I do not have a paranoia or something similar, but I want  convenient way to store passwords (I have couple of hundreds) and use them daily whenever needed.

Another great tool which is lacking in automation of loggin process is SecureLogin FF extension - [https://addons.mozilla.org/ru/firefox/addon/4429](https://addons.mozilla.org/ru/firefox/addon/4429). I stopped using it because I wanted to try to use LastPass.

Other password managers which are available via Synaptic or source packages over the web (as far as I have found) are no good at all. These pieces of software are usually and standalone program which does not fill forms automatically and does not integrate itself to the FF, which is the main browser in Ubuntu Gnome. 

Once again I am asking Ubuntu community to share thoughts - is it worth using LastPass,and can we trust this small or big (I do not care) company? It is a bit useless to ask this question somewhere else since most of the WIN users do not wish to think of that.

Thanks a lot guys

---

### Post by RRFarFar on 2008-10-02
I guess the answer is - WE DO NOT KNOW:))))), isn't it?

---

### Post by JoeSiegrist on 2008-10-02
> **RRFarFar said:**
> All right, I guess most of you are familiar with the web service called LASTPASS - [https://lastpass.com/](https://lastpass.com/). There is an extension for firefox and it work in linux - [https://addons.mozilla.org/ru/firefox/addon/8542](https://addons.mozilla.org/ru/firefox/addon/8542)

I doubt most people know about LastPass yet, as we here at LastPass have only had a beta out for ~6 weeks.  We'd recommend you download off [https://lastpass.com/](https://lastpass.com/) rather than on addons.mozilla.org.   AMO hasn't had a chance to review us so that version has no updates (when you're stuck in the AMO sandbox you get no updates, a known issue with AMO).

> **RRFarFar said:**
> Like in a foxmarks service we can use sync tool to have our passwords across several PCs. Since I am using ubuntu I would like to ask this question here, although it is not related to Ubuntu Linux in a pure sense. The reason why I am posting it here is to ask people of the alternatives and trustworthiness to such services. Can it be trusted??? 
As far as my opinion, this service is very convenient to use, but how are they keeping it alive? Where is the source of their money? Maybe they are using this service for marketing and some other purposes?? Who knows....

We're a group of programmers who have Linux (Ubuntu of course), Mac and Windows PCs, and see a problem with how passwords are handled today.   We're really at the beginning of what we've planned for LastPass and are making every effort to ensure that you always have access to your sensitive data (and that LastPass never has access to it).  We should have LastPass pocket out for Linux very soon.  We've answered the 'how will we make money' question before on [https://lastpass.com/faq.php](https://lastpass.com/faq.php). 

> **RRFarFar said:**
> 
Once again I am asking Ubuntu community to share thoughts - is it worth using LastPass,and can we trust this small or big (I do not care) company? It is a bit useless to ask this question somewhere else since most of the WIN users do not wish to think of that.

We'd like to think we're trust worthy: we've consistently made moves to protect our users at the expense of ease of development and reduced knowledge about our user base.  We've made exporting back to Firefox or to a CSV file just as easy as installing.  We're doing what we think is right by the user; how we'd expect it to be built if we were looking for an accessible password management solution.

Joe Siegrist
LastPass

---

### Post by RRFarFar on 2008-10-03
That is exactly what I wanted, THANKS VERY MUCH for the reply. Ubuntuforums is again the only source where users can read the things not found anywhere else on the web
As I have written above I do not have a paranoia regarding passwords being stored somewhere else, other than my LPC (I like to call it Linux Personal Computer). 
Anyhow, would you describe the way data is stored on you servers? I guess this data is stored in an encrypted form? The ideal situation would be when the data is stored in an encrypted way when a user has a certificate which guarantees that it is only him who has an access to data. From the technical point this might sound like utopia)))) - to much technical difficulties, but from the point of user trust it looks very promising. Do you agree?
When do you come out of the BETA?
This is not an interview, this is just the things a user wants to know (at least me) - Where are you heading to in a future and what one may expect from your service, since some users may start using LastPass quiet extensively
(Sorry for my English, I guess there are a lot of mistakes;))))))

---

### Post by lovinglinux on 2008-10-03
I have installed lastpass after reading this thread and I think is very good, so far.

I haven't tested with hundreds of passwords, but I guess the site list should also have the grouping feature. Additionally, it doesn't have a way to import/export passwords from/to Revelation Password Manager.

Aside from the privacy concerns, the most important feature is the ability to export the passwords even if the service is down or discontinued. This gives some peace of mind compared to other services out there.

BTW, nice to see a reply from the developers here.

---

### Post by hyper_ch on 2008-10-03
Basic rule of secrurity is: Trust no one and nothing.

However for storing login data to forums and other "harmless" stuff I think you can trust certain third parties. However I advice to NOT store bank account data and such stuff there.

---

### Post by JoeSiegrist on 2008-10-03
> **lovinglinux said:**
> I have installed lastpass after reading this thread and I think is very good, so far.

I haven't tested with hundreds of passwords, but I guess the site list should also have the grouping feature. 


You can group your accounts (it's under preferences).   Though it doesn't happen until you hit 20 accounts by default.

> **lovinglinux said:**
> 
Additionally, it doesn't have a way to import/export passwords from/to Revelation Password Manager.

If you'd like to send the the export format of Revelation Password Manager with your private data replaced/removed to [email]support@lastpass.com[/email] we'll look into supporting it.

> **lovinglinux said:**
> 
Aside from the privacy concerns, the most important feature is the ability to export the passwords even if the service is down or discontinued. This gives some peace of mind compared to other services out there.

BTW, nice to see a reply from the developers here.

Glad you noticed that -- we spent a lot of time making sure that the product is still usable even if we're not available, and always exportable. 

Joe Siegrist
LastPass

---

### Post by JoeSiegrist on 2008-10-03
> **RRFarFar said:**
> Anyhow, would you describe the way data is stored on you servers? I guess this data is stored in an encrypted form? The ideal situation would be when the data is stored in an encrypted way when a user has a certificate which guarantees that it is only him who has an access to data. From the technical point this might sound like utopia)))) - to much technical difficulties, but from the point of user trust it looks very promising. Do you agree?

All your sensitive data (name,username,password,group, any form fill data) has been locally encrypted on your PC, using a key that only you have (your key and your master password are never sent to LastPass).  We still send data to LastPass using https, even though it's already encrypted and useless to everyone including LastPass. 

We also have some data that we often need like your login email (which is stored unencrypted) and your password hint (which we store encrypted using a LastPass key).

It probably would be ideal to use a cert but we think it's beyond what average people are going to deal with so we think we've struck a nice balance -- creating a key from your email and password using Javascript allows you to have access to your data even online while knowing that no one else has access.


> **RRFarFar said:**
> 
When do you come out of the BETA?


We're not sure; we're likely not too far from it.  We know we need to build a 64-bit linux plugin though --  Our userbase has primarily been Windows and Mac so far, so we're hoping to get good feedback from you guys to see how close we are in the Linux world.

Joe Siegrist
LastPass

---

### Post by RRFarFar on 2008-10-03
> **lovinglinux said:**
> Aside from the privacy concerns, the most important feature is the ability to export......
What does that mean anyway???? Aside or not aside. Export import thing is just a temporary inconvenience, they will certainly do this in future. Also, this service will not be discontinued in a near future, I guess that should be supported by common sense, otherwise it makes us very vulnerable, most of the web service providers are here to stay, and they are very unwilling to leave the market. As far as this lastpass.com website tells us, they have some large corporations as their customers.
You know what, I think I doing a marketing role here - LastPass promotion in ubuntu forums.
;))))

---

### Post by RRFarFar on 2008-10-03
Hie Joe,
> **JoeSiegrist said:**
> All your sensitive data (name,username,password,group, any form fill data) has been locally encrypted on your PC...
Where exactly in ubuntu does my FF extension stores that data?
> We still send data to LastPass using https, even though it's already encrypted and useless to everyone including LastPass.
You are saying that the data is useless for anyone, even you, but in the next paragraph you are saying that some data goes unencrypted. Can it be possible??? HTTPS connection mean that everything in securely encrypted. 
> We also have some data that we often need like your login email (which is stored unencrypted) and your password hint (which we store encrypted using a LastPass key)

The whole scheme is still uncertain to me. I beg your pardon, but it would be great if you could explain.

Thanks

---

### Post by JoeSiegrist on 2008-10-03
> **RRFarFar said:**
> What does that mean anyway???? Aside or not aside. Export import thing is just a temporary inconvenience, they will certainly do this in future. Also, this service will not be discontinued in a near future, I guess that should be supported by common sense, otherwise it makes us very vulnerable, most of the web service providers are here to stay, and they are very unwilling to leave the market. As far as this lastpass.com website tells us, they have some large corporations as their customers.
You know what, I think I doing a marketing role here - LastPass promotion in ubuntu forums.
;))))

I appreciate your help but wanted to clear up some things -- we don't have large corporations as customers yet, but we've done that before at previous jobs and see a need that we will try to fill with LastPass. 

The general privacy points around LastPass are around the data you share with LastPass -- e.g. your email address (you can use a fake one, we don't check it, but notifications can be setup to be sent on actions, so we recommend a real one).  

You can increase your privacy by turning off features, (e.g. disabling login history) we've written up a privacy policy that tries to make that clear.

It should be noted though that we locally encrypt your sensitive data and do not have the key, so the privacy implications here are far smaller than your typical web application.

Joe Siegrist
LastPass

---

### Post by lovinglinux on 2008-10-03
> **JoeSiegrist said:**
> You can group your accounts (it's under preferences).   Though it doesn't happen until you hit 20 accounts by default

Oh, sorry. I have tested it with just a couple of passwords :oops:

> **JoeSiegrist said:**
> If you'd like to send the the export format of Revelation Password Manager with your private data replaced/removed to [email]support@lastpass.com[/email] we'll look into supporting it.

Thank you. I will do that.

> **RRFarFar said:**
> What does that mean anyway???? Aside or not aside. Export import thing is just a temporary inconvenience, they will certainly do this in future. Also, this service will not be discontinued in a near future, I guess that should be supported by common sense, otherwise it makes us very vulnerable, most of the web service providers are here to stay, and they are very unwilling to leave the market. As far as this lastpass.com website tells us, they have some large corporations as their customers.
You know what, I think I doing a marketing role here - LastPass promotion in ubuntu forums.
;))))

Sorry for my bad English. I was trying to say "apart from privacy concerns", because privacy is the most important issue to be considered. Anyway, I strongly disagree with your statement. Most web service providers are unwilling to leave the market, but we have several examples of big and small companies closing their web sites or specific services, sometimes even without warning. For instance, Yahoo is closing  it's music store [(view article)]("http://www.switched.com/2008/02/04/yahoo-exits-the-music-biz/"), DivX closed Stage6 video hosting web site [(view article)]("http://news.cnet.com/8301-10784_3-9891761-7.html"), Veoh definitively blocked access to 33 countries without warning due to new business strategy [(view article)]("http://newteevee.com/2008/06/01/veoh-blocks-some-international-access/") and a quick search on Mozilla Add-ons web site will reveal dozens of extensions not supported on version 3.x. I wish that LastPass achieves the business success they are expecting and stay available for a long time, but knowing that I can export my passwords anytime, even without internet access, is priceless.

---

### Post by excbuntu on 2009-03-07
> **JoeSiegrist said:**
> All your sensitive data (name,username,password,group, any form fill data) has been locally encrypted on your PC, using a key that only you have (your key and your master password are never sent to LastPass).  We still send data to LastPass using https, even though it's already encrypted and useless to everyone including LastPass. 

We also have some data that we often need like your login email (which is stored unencrypted) and your password hint (which we store encrypted using a LastPass key).

It probably would be ideal to use a cert but we think it's beyond what average people are going to deal with so we think we've struck a nice balance -- creating a key from your email and password using Javascript allows you to have access to your data even online while knowing that no one else has access.


so. i understand that the key can be obtained by knowing the e-mail and password. since you know our e-mail, all you have to do is guess the password via a script to generate a key. after running the script a couple of days you'll eventually have the correct password and key combination. and now you have access to our data?

i'd completely trust the program if it gave me the *option* to upload my encrypted data to your servers and leave my data on my local computer only (like roboform). or i'd completely trust your servers if you guys used the certificate authentication that is popular with ssh connectivity as described by lovinglinux in an above post. with 123-instructions, it shouldn't  be hard for "average people" to use.

---

### Post by JoeSiegrist on 2009-03-07
> **excbuntu said:**
> so. i understand that the key can be obtained by knowing the e-mail and password. since you know our e-mail, all you have to do is guess the password via a script to generate a key. after running the script a couple of days you'll eventually have the correct password and key combination. and now you have access to our data?

If you pick a decent LastPass master password you can replace 'a couple of days' with 'until the end of the universe'.   It's encrypted with AES-256. 

> **excbuntu said:**
> 
i'd completely trust the program if it gave me the *option* to upload my encrypted data to your servers and leave my data on my local computer only (like roboform).

This is coming.

> **excbuntu said:**
> 
or i'd completely trust your servers if you guys used the certificate authentication that is popular with ssh connectivity as described by lovinglinux in an above post. with 123-instructions, it shouldn't be hard for "average people" to use.

This is also coming, but I think you overestimate what 'average people' can and will do here.  Could/would your mother do this?  Maybe your average linux user...

Joe

---

### Post by randyklein99 on 2009-04-27
Just a bump to see if there's any new development to talk about...

---

### Post by randyklein99 on 2009-04-29
Another question:

Is the password we use to login into lastpass.com supposed to be the same that we use locally to "authorize" a password fill?  Because if so, don't you already have half the equation to decrypt?

Edit:
so like most of my posts, I seem to find the answer after posting.  Here's a lastpass forum link that covers this exact topic:
[http://forums.lastpass.com/viewtopic.php?f=6&t=4389]("http://forums.lastpass.com/viewtopic.php?f=6&t=4389")

Although the encrypting verbiage is over my head, it sounds reasonable.

---

### Post by rykel on 2011-10-03
I am a Premium member of LastPass and XMarks, and anyone long enough on this Ubuntu Forums know that I am a Linux guy. While I find XMarks to be somewhat redundant, I cannot live without LastPass. It is that GOOD. I cannot say for sure that they themselves are NOT thieves of passwords, but until there is a better solution, I have to trust them.

---

### Post by Rubi1200 on 2011-10-03
Thread closed.

Reason: necromancy

---

