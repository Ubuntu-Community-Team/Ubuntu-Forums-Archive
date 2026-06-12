---
title: "whitelisting in Ubuntu CE"
date: 2012-12-25
forum: Ubuntu Christian Edition
---

### Post by Charles-2007 on 2012-12-25
I like the look!  I've been doing some trials of various flavors of Linux in an attempt to build a web station that can be (fairly) unsupervised in a church library.  I am thinking it might be preferable to whitelist web sites rather than blacklist.  That evidently can be done in Dansguardian filter and Privoxy proxy but it looks pretty painful.

If someone smarter than me could write a HOWTO that a Noob could understand to get whitelisting, it would be much appreciated!

Best wishes.

---

### Post by vasa1 on 2012-12-25
I don't know about Dansguardian, but why do you think whitelisting via Privoxy would be difficult? From what I read casually, it's just a matter of having a trust file (/etc/privoxy/trust) and editing /etc/privoxy/config appropriately. I don't know if Privoxy's trust file will apply to http**s** sites. A lot of Privoxy actions don't apply to http**s** sites.

But, as always, it depends on how savvy the "opposition" is :) One example is with Firefox. In Preferences, Advanced, Network, any user can simply choose not to have Privoxy as a proxy server. Game over. Unless you take measures to prevent users accessing their profiles. I don't know whether stability will then be affected.

With Chrome, the user can just start Chrome from a terminal with the --no-proxy-server switch.

---

### Post by Charles-2007 on 2012-12-27
I am going to mess about with all this further and if I get something that can be reproduced with some ease I will post it.

I am building an OPAC station (library card catalog) in a church.  There are many discussions of this online, many involving complex interventions like recompiling ISO disks.  If I can get it done on Ubuntu then the librarians can log on and use OpenOffice.  I plan to create an autologon user with very limited options.

We got plenty of kids roaming about who could probably figure out how to run terminal ... this is the challenge.

Best wishes.

---

### Post by c4c on 2012-12-30
This was for Ubuntu 10.04, so I don't know if anything has changed. Also, I admit to not trying this myself.

For complete control over the web sites a particular computer can see, *you can*...
      [COLOR=#3333FF]**Easily BLOCK access to *EVERYTHING* on the Web EXCEPT what YOU say**[/COLOR]
      [COLOR=#FF0000]*Warning: this is a drastic measure and can be painful to change/update*[/COLOR]
      
      [COLOR=#3333FF]**1.**[/COLOR] Find the IP addresses of the sites you want to access.
      *Easiest way is through this site       [http://ip-lookup.net/domain.php](http://ip-lookup.net/domain.php)*
      
      **2.** Copy the IP address, the domain name and the domain name with "www" in front of it into a text file, then...
      
      **3.** Go to **Applications --> Accessories --> Terminal**
and type (or copy and paste): **sudo gedit /etc/hosts**[COLOR=#FF0000][Enter][/COLOR] or [COLOR=#FF0000][return][/COLOR]
      
      **4.** Add one line for each of the sites you want the computer to be able to access
      *Example:*
12.10.241.10 comeashelter.org [www.comeashelter.org](www.comeashelter.org)
64.71.40.27 cheyennehealth.org [www.cheyennehealth.org](www.cheyennehealth.org)
208.90.190.159 cheyennecity.org [www.cheyennecity.org](www.cheyennecity.org)
137.87.0.106 lccc.wy.edu [www.lccc.wy.edu](www.lccc.wy.edu)
      *Save the file, and "X" out of it*
      
      **5.** Type (or copy and paste): **sudo gedit /etc/nsswitch.conf**[COLOR=#FF0000][Enter][/COLOR] or [COLOR=#FF0000][return][/COLOR]
      *find the line that looks like this*
      **hosts: files dns**
      *and change it to this*
      **hosts: files**
      *Save the file, and "X" out of it*
      
Close and reopen the browser and the computer will be cut off from *EVERYTHING* on the internet except for the sites you have listed in step 4.
      
      [COLOR=#006600]***Note:***[/COLOR]* if using **Leafpad** instead of **Gedit**, simply replace the word **gedit** with the word **leafpad**.*

---

### Post by nixblog on 2013-01-02
> **Charles-2007 said:**
> I like the look!  I've been doing some trials of various flavors of Linux in an attempt to build a web station that can be (fairly) unsupervised in a church library.  I am thinking it might be preferable to whitelist web sites rather than blacklist.  That evidently can be done in Dansguardian filter and Privoxy proxy but it looks pretty painful.

If someone smarter than me could write a HOWTO that a Noob could understand to get whitelisting, it would be much appreciated!

Best wishes.

If it's a web based kiosk setup you have in mind then look at [Webconverger]("http://webconverger.com/") and use it in conjuction with a web based blocking service such as [OpenDNS]("https://www.opendns.com/").

---

