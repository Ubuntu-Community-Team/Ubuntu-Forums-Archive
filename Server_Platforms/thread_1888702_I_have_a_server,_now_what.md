---
title: "I have a server, now what?"
date: 2011-11-29
forum: Server Platforms
---

### Post by ffixcollector on 2011-11-29
I just picked up a [[COLOR="Blue"]Intel SE7520BD2[/COLOR]]("http://www.geeks.com/details.asp?invtid=SE7520BD2-K1-R") set up with 10.04 Server. I just got done installing PS3MediaServer and Deluge, for a seedbox and transcoding server. The only problem I have is that mencoder only utilizes 70% across all 4 cores(280% total). Any ideas to fix this? I hope to have 8gb of RAM installed by the end of the week. I also have a LAMP stack, and a few others I added during install.

What else can I do with this unit? I was thinking to maybe cluster it to off load CPU from my desktop.

How can I utilize my RAM? I will have 8gb! What do I do with it? What do the Guru's suggest?

---

### Post by arrrghhh on 2011-11-29
What do you want to do with the server...?

mencoder utilizes as much CPU as is needed - are you saying it should use more, or less...?

To use more RAM, VM's are always a good option....  You haven't really given us much to go on tho.

If you're looking for what other people use their servers for, there's a HUGE amount of options.  I personally use mine as a file/media server.

---

### Post by ffixcollector on 2011-11-29
I am looking for a way to dive into all the options, weekend projects, ect. I also use file/media sharing, and hope to use apache to share my files with family. I don't like the idea of wasting power just to run deluge. I wish there was a list of common server setups that could be used from the day to day. Stuff that can give me experience managing a server, and options that can allow me to possibly sell ready to go servers to my clients. Not many small business need a LAMP stack. I would like to know what others use their servers for, to give me ideas on the possibilities of what I could do with mine. FreeNAS was great, but its time to move on.

I've thought about VM's, but am not sure how I could use them day to day. I also considered a PXEboot server, but I don't want to rely on my server for DHCP.

---

### Post by arrrghhh on 2011-11-30
You can setup PxE while still using your router as a DHCP server.

LAMP is a good thing to know for a lot of jobs.  You could spend your life specializing in MySQL for example :p.  Some will want stuff like OpenLDAP or some sort of authentication method to access files from workstations.  DNS servers for the LAN is another thing that a lot of companies will care about.  Obviously for smaller companies, they might be interested in some open source groupware for sharing content.  There's another thing to look at, content management systems.  

VM's would be a good thing to practice, just to get the hang of how they work and how you interact with them - another thing you could spend your entire life specializing on.  Although most larger companies I've worked with seem to use ESX-i...

I guess if you want to just find what servers are capable of, search around what people are posting about in this section.  Sounds dumb, but you'll see what people are working on.  Might give you ideas of stuff to play with...

Plus, the Ubuntu community pages are priceless.  Spend a few days in there and you'll have plenty to do ;).

---

### Post by ffixcollector on 2011-11-30
Thanks, I never thought about the Ubuntu community pages. 
I do wish there was a similar source for updated and beta software. [[COLOR="RoyalBlue"][COLOR="Blue"]Subsonic[/COLOR][/COLOR]]("http://www.subsonic.org/pages/installation.jsp#debian") looks like a cool application. Its just difficult finding and in some cases installing these newer apps.
The Webmin plugins are giving me some great ideas as well.

---

