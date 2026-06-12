---
title: "Ubuntu server as mail gateway/port forwarder"
date: 2016-12-12
forum: Server Platforms
---

### Post by mad.scientist2 on 2016-12-12
hello folks... I have a bit of a techinical conumdrum.,.. im not sure how to get out of.  my skill with linux is moderate at best.

TO start, I followed a guide on ars  technica to setup a mail server. This unit works just fine.   however. I do have  the standard problem of the blocked ports with the ISP so  I have not taken the server live yet.

What I would like to do, and therefore to know if it is possible, Is to piggyback onto a server at my company, that has a business class connection.

In other words, the mail server would still be located physically in my home, but it would route through  another gateway server at another location. 


i do not want the gateway server to do any kind of email processing, scanning, av, firewall, anything. I simply want it to push the emails out to the web based on the data given from the home server.


Is something like this possible? and if so, what would it require?  please feel free to get technical.   I have considered possibly using a vpn as the simplest solution but would need to figure out the configuration.  Secondly, i thought there might need to be some sort of application running such that the home server would only be transmitting standard network data to the gateway, and another application on the gateway would push the data out... again.. not sure how it would work.   just to reiterate.. the gateway should do NOTHING to the email but distribute it. it should also not create any logs, scan for spam.. etc.  


Thanks in advance for your replies!

---

### Post by SeijiSensei on 2016-12-12
Unless you can convince us that you have permission to use a server at your company, [we probably cannot help]("http://ubuntuforums.org/misc.php?do=showrules") under the no-circumvention provision.

---

### Post by oldos2er on 2016-12-12
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") is right; this is something you'll need to take up with your company. "it should also not create any logs, scan for spam.." is suspicious, to say the least.

Thread closed.

---

