---
title: "ispConfig - Website configuration"
date: 2006-05-13
forum: Server Platforms
---

### Post by izzyonstage on 2006-05-13
Hi,

I am relativly new to ubuntu and linux in general, but i have followed the How-to's around and have managed to set-up my ubuntu as a web server. I have Apache2, ispConfig, and all extras except for vbscript and asp support. What i want to do now is create the main web site that will control my server to allow my friends and family to log on and create, edit, and upload there sites. I am also looking to see if it is at all possable to get a vbscript and asp parser for my set-up.

Hope someone can help me.

---

### Post by Socratez on 2006-05-14
Doesn't the ISPconfig install a admin page to <yourserverIP> followed by :81 ? I could be wrong but I think there is a management interface when you connect to port 81 ... I am in the mist of installing the ISPconfig as we speak and I am almost certain that is what I had read during the install ...

---

### Post by izzyonstage on 2006-05-15
Well yes it does, but for some reason since i have added a reseller and a client to my ISPConfig list I cant access it. All I get is a shared ip page. And my domain name doesn't work either.

---

### Post by Socratez on 2006-05-15
I had a simliar problem with my ISPconfig ... I added a test reseller and test client and then my default apache was no longer working ... I think it is due to the apache2 being running as well as the apache 1.3 the ISPconfig installs ... I am not certain though ... still working on it to no avail thus far ....

---

### Post by izzyonstage on 2006-05-16
I think that because i have a bt router i cant type my IP address from inside the network as it just takes me to the router settings, and for some reason i cant use the computers internal IP either which just comes up with a warning box saying i have not got authorization to access that ip. but if i use 127.0.0.1 then it works. so i have now taken off the reseller and client, and it works again. All i need to do now is register my DNS server so i can use my own dns server to host my domain name. Also need know how to install the webmail add on. cant seem to get it working, and find out why when adding a reseller it goes wrong.

---

### Post by Socratez on 2006-05-16
[FONT=Georgia]**I added the add-on packages right from th ISPConfig site and use the Update tool to install them .... I am not sure how to get them to work from there but it worked smooth as can be for me. I installed PHPMyAdmin and the second webmail server listed ...  **[/FONT][B][FONT=Georgia][B]RoundcubeWebmail .... 

My problem is DNS too as I figured out later on today ... I have no clue how to do DNS but I am gonna give it my all ... Shouldn't be too hard once I get the hang of it ... [/B][/FONT]
[/B]

---

### Post by izzyonstage on 2006-05-20
how did you install these pakages, i have downloaded them but my installer from the tools menu wont install them. all i get is the pages comming up as text not as the parsed page.

---

