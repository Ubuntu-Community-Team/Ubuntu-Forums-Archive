---
title: "Does anyone know of a network monitor app for measuring download usage?"
date: 2008-05-21
forum: Server Platforms
---

### Post by garethsimpsonuk on 2008-05-21
Can anyone recommend a monitoring tool for measuring total download usage? Ive been looking around and have found quite few but would like some opinions.

I run gutsy with samba / lamp and torrentflux the thing is virgin.net in uk have a fair usage policy which I seem to break if im not careful. This is mainly down to using torrents between 5 - 2 pm. 
I would like to watch how much bandwidth each box is using with daily / weekly monthly stats.

I start x gnome when I need to but it's usually headless so a GUI would be nice but even better a web gui like webmin / PHPmyadmin .

I don't really want a cmd line only app.

Cheers

---

### Post by arsenic23 on 2008-05-21
Well, I can't think of a good non CLI tool.  But I can recommend vnstat, as it is very easy to setup and use.

Just *[COLOR="DimGray"]vnstat -d[/COLOR]* for daily, *[COLOR="#696969"]vnstat -m[/COLOR]* for monthly, and *[COLOR="#696969"]vnstat -h[/COLOR]* for hourly.

---

### Post by Patb on 2008-05-22
Gareth, I'll give a second vote for vnstat.  Couldn't you have it run the output to text which you could then incorporate into a web format?  Not my field, so I can't say how but it would seem easy for someone competent.

Cheers, Pat.

---

### Post by Onesimus on 2008-05-22
You could also use gkrellm.  It has a network monitor on it.  By clicking on the small square in the right hand corner of the network window, a new window appears displaying the upload/download usage for daily, weekly and monthly.

gkrellm is also able to monitor a lot more of the system (e.g. temperatures, etc. etc.)

---

### Post by garethsimpsonuk on 2008-05-22
Thanks for the replies guys, yea I've heard of vnstat. A cli app would probably be better for viewing remotely if there is no web gui. 

I think I'll go with that one. One question though will it tell me a totals of all the boxes on the network?

Virgin look at everyones usage each week and they then throttle down to 256kb/s the people who are in the top ten percent for a week and so on. So I need to work out an average of what will keep me below the threshold.

Will vnstat provide this? 
PatB that sounds like a good idea I guess someones probably already wrote a script for this already. It's beyond my skills. 
Would it be best done in bash? I could then write a php script to display the output on my home website.

Just a thought do people write there own webmin modules / addons? Is it open source? I'm gonna have google and find out.

Cheers guys

---

### Post by garethsimpsonuk on 2008-05-22
I've just come across a ubuntu page I didn't know was there. This seems to have some links for net monitor apps.

[URL="http://https://help.ubuntu.com/community/Servers"]

---

### Post by garethsimpsonuk on 2008-05-22
Whoops, and I'm supposed to be a web designer, struggling with bbcode 

[https://help.ubuntu.com/community/Servers]("https://help.ubuntu.com/community/Servers")

---

### Post by shibu on 2008-05-22
a few more ....


ifstat - InterFace STATistics Monitoring
iftop - displays bandwidth usage information on an network interface
ipband - daemon for subnet bandwidth monitoring with reporting via email
iperf - Internet Protocol bandwidth measuring tool
ipfm - a bandwidth analysis tool

---

