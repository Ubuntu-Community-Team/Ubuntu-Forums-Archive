---
title: "apache2 how to make custome errors...."
date: 2008-09-13
forum: Server Platforms
---

### Post by hockey97 on 2008-09-13
Hi I want to make custome errors like 404 ect and also I want to turn off apache2 settings that allows to broadcast the apache2 server info like the version and the addons ect.

I just want to help stop apache2 from giving out information that a hacker can use it for a breakin like the server name saying apache and the version and the mods that had been added.

thanks.

---

### Post by windependence on 2008-09-13
You're being paranoid here but I'm gonna tell you how to do it. All of this is in your apache2.conf file. The custom messages are all there and all you need to do is change them and uncomment them. The other info is there too. In that case you want to comment out the lines you don't want to show that contain server information. 

Just FYI, I have had this information visible for 4 years now on our sites with no break-ins. We get hammered by thousands of attempts daily, but they don't get in.

-Tim

---

### Post by hockey97 on 2008-09-13
thanks. I know a few hackers and have talked to them and learned how to kiddie hack.

kiddie hack is just like kiddie scripting.

I learned alot and one think I learned is that info is valuable what kiddie hackers do they look at this info and then do a google search for security holes and even they are on black market fourms that talk with each other true hackers finds security holes kiddie scripters just learn what security holes there is from true hackers and then they use tools or create a script that would do the attack.

So if you have a version and apache finds another security hole and somehow you were late on updating it you may get attacked one day.

this is why I am very strict on security. 

I found in the config the place were you can turn on and off the version broadcast.

Mine was one so I switched it to off.

now I tested it after restarting apache and looks great.


I would just say that the best say to avoid alot hacking attacks is to admit or say that you don't know everything in the computer world because if you do say that your not hackable you just bring on a challenge.

---

### Post by windependence on 2008-09-13
I never said I was not hackable, show me where. After you'r all done with this if you give me the ip of your site I'll still tell you what you're running and even your OS version. ;)

-Tim

---

### Post by hockey97 on 2008-09-13
yes I am aware of network tools that you can still find out what version I am running ect.

however I am still working on my website. I plan to switch from default ports except for apache website port 80.

I know of network maps.

I never said you said that your hackable but I am just saying that you are still hackable and makes it a little easier to find out what web server your running.

Even the network mapping tool you can't find 100% the stuff it makes guesses unless the person has used default ports.

I am arguing but just want to extend my knowledge on security.

like you said you never was hacked in 4 years.

I do bealive  you and I myself might not even get hacked in 4 years or other years to come.

true hackers only target any website that is worth hacking into like the website should contain alot of personal info that is valuable which is like credit cards ect ect.

SO most hackers do just attack valuable websites.

then kiddie hackers hack websites to show off those usally you can avoid by not making it very easy for them to break in.

I am just saying this is why I am trying to make my website as secure as possible.

I also wounder how would someone go about reporting a hacker that hacked your website???

someone hacked into my friends account one time and added another cellphone which they called many places leaving a big bill to my friend which he then went tot he local police station and filed a report he cops were lol and told him that they have more important crimes to deal with like murder and bank robbery.

:) I am not saying your saying your unhackable but I am just explaining why I wanted to remove the apache broadcast.

It also would make you look unprofessional since once you see and know that the person runs apache a free webserver they would think it might be some kids running a server.

I notice face book runs apache2.


I also thank you for helping me.

---

### Post by windependence on 2008-09-13
Well in all fairness I don't run my sites on Linux, they are all *BSD. Why? because it is the most secure OS on the planet. On OpenBSD sites, you can't even tell what OS I am running. I can tell you haven't got much experience with this stuff. I'm not trying to talk down to you, just trying to save you from wasting your time. Most webhosting n00bs are scared to death they will be hacked, but unless you are using Windoze it's really rare. On the server signature, it won't make you look like an amateur. I have seen and atually ran several very large corporate web sites where you could see the Apache version if there was an error. The reason we didn't bother taking it out is because it really is just a waste of time. If you want real security, invest in a good firewall/UTM box to put in front of your network or even build it yourself using something like pfsense (which runs OpenBSD).

Anyway, if you need any more help with the server just post here. We have a lot of good people here and I also hang out on this forum. I have been a Unix sysadmin for several years, and I run commercial servers for a living. Would be glad to help you.

-Tim

---

