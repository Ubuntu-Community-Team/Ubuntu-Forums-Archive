---
title: "webmin help please..."
date: 2007-05-16
forum: Server Platforms
---

### Post by hockey97 on 2007-05-16
HI I have webmin the latest version, and I installed squid proxy server by using webmin to install it and I click the start server button and it faild to start it gives me an error.

here is the error

2007/05/16 00:18:14| parseConfigFile: line 4361 unrecognized: 'httpd_accel_with_proxy off'
2007/05/16 00:18:14| parseConfigFile: line 4362 unrecognized: 'httpd_accel_uses_host_header off'
2007/05/16 00:18:14| parseConfigFile: line 4363 unrecognized: 'httpd_accel_single_host off'
FATAL: No port defined
Squid Cache (Version 2.6.STABLE5): Terminated abnormally.
CPU Usage: 0.008 seconds = 0.004 user + 0.004 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0


I played wtih those values the only thing I could do is hit yes or no and I tried both like at a time
like one time with yes then one time with no and still gives me the same error.

the fatal no port defined I played around and put port 80 or 8080 and that stoped the error.

What I plan to do is to have a proxy server that is in ssl mode so that I can connect from my school to bypass their  proxy settings ect 

How does squid porxy work. like is their an interface on the web??  I do have a php script that does or acts as a proxy server but at school I can't get flash or java media I can only get website's how ever this is not secure becuse the IT found out what we were doing.

SO I need some way to protect me by not having the IT people able to track me using my proxy.

I also would love to know how I can connect from my school to my server to see my desktop and do some work.

I mean like I have windows xp at school and I want to be able to play games from my hard drive I have xp and home that is dual boot with ubuntu 7.4

I want to be able to play my games from my xp windows is that possible??

it would be great if I could do that., Like I don't want to have to install the game on my computer at school more want to act as if I am using my computer with xo at home but yet it's at my school.

Like I want to be able to view my desktop at home and click applications and see them run.

but any saves or running of applications would be still handled from home.

but the thing is I have one computer and I know that I need linux for the server ect  and but I want to use xp for programs.

I do have ntfs support with ubuntu.

basicly want to be able to use my interntet at home and also the games at my home I want to be able to play them without installing it on my computer at school, so the game will run

off my computer at home but I want o have control and able to play with it kinda like a live stream of my computer so I can play games that are not on my computer at school but play off my computer at home which have the games installed.

The reason is becuse my school dosne't allow any games being played and I am in an eletronics class and we have spare time to go on and play games ect our teacher let's us.


I use ubuntu as a server type thing and plan to keep using it as a server but yet want to be able to play games and use applications off my computer at home with the Windows XP partition. 

on ubuntu I can see my hard drive that is Xp and has all my windows applications, do you thing since my computer at school has windows xo that if I can connect to my computer at home
that has the ubuntu server ect well server's, that if I can see the desktop of ubuntu of my computer at home that I can click the applications of Windows xp and should it run??

I don't plan to install these apps on the computer at school at all. I just want to run the game's off my computer which is dual booted one in ubuntu and one in Windows Xp but the games are windows or on my windows hard drive and I am not sure if in ubuntu they could run.

I really want to run the game off my computer with the dual boot and want to just stream the data so I could play the game at school while I don't have the game files on my computer school but the files are on my computer at home witch is installed and working but dosen't work with ubuntu can't open it but I use ubuntu for the server and need to run windows XP at the same time Ubuntu is running.

I hope this clearifies what I want or need ect.

Thanks in Advance.

---

### Post by hockey97 on 2007-05-16
Does anyone know how to setup a squid proxy??

I want to be able to use an ssl to securly tunnel to my computer at home.

Has anyone got or know way's to have a proxy server able to run java app's or flash I have a proxy script but it works only for websites any flash or java content would not load becuse the site is blocked.

---

### Post by hockey97 on 2007-05-18
Hi I really need help with squid proxy I think I need to reinstall it becuse it give's me erros of the code on lines like 144 or somthing in that order and what ever input I put weather it's on or off that it still spit's out the same error's but at the main site for squid proxy they say that you don't need to config anything which I didn't and I get these error's still.

Can someone help me??

---

### Post by hockey97 on 2007-05-20
what is squid proxy??

I really need help setting up this proxy server I know it's not illegal.

---

### Post by ricrac on 2007-05-20
I do not wish to offend you, but they me explain from the School's sysadmin's point of view.

The controls/restrictions were put in place to keep the system more secure and often primarily to throttle the amount of data on the local network.  Flash, Java games, remote desktop can all be data intensive.  

While proxy/filtering the school can:
Block sites known to be attack vectors
Block protocols known to be attack vectors
Virus scan downloads and email attachments before they get into the local network
Use intrusion detection and actively block worm's, bots, or "script kiddie" hacking
Reduce unwanted traffic crossing onto the local network, movies, music, games, porn, etc.
Identify and monitor bad citizens on the local network who are abusing everyone elses resources.
Discourage miss-use of school resources for non-academic purposes.

In short, to do all you describe squid will not suffice, it would do the java and flash games.
If you get caught, you should be suspended, fined, lose grant or scholarship, etc.

If you want unmanaged access, move off campus and get your own dsl.  Again, I do not mean to sound harsh but you are trying to break the school's rules. Period.
Oh, and your electronics class teacher should be reprimanded, and if he still encourages students to break school policy, he should be fired. Period.

If you don't agree with the policy, take it up with your student council or school administration and get the policy changed.

Any of the below would be a better use of spare time in electronics class.
atlc, drawtiming, electric, geda, kicad, ksimus, ktechlab, linsmith, nec, oregano, transcalc, vipec, x10, girls, boys, whatever you're into.

Spare time in class???

---

### Post by hockey97 on 2007-05-21
I see.  Well First off I am not fully doing it for myself the kids in my class are pushing me to do such  a thing.
and The IT people are not that fully smart really,  like their blocking AVG website's and also the update's.

Their  using forty guard to block the stuff,  the students just want to play flash games ect, in the begining of the school year they havent block this stuff ,   the system anyway's crashe's becuse our attendance and grade program called sassy alway's crashe's, I also was able to shutdown the school's server for 3 hour's and the IT people were in the dark they didn't know what happend, I have been messing with them becuse they came on my computer one time becuse I had blender and the raytracer render engine they thought that the raytrace was some sniffing tool so they were trying to accuse me of hacking or sniffing then network they hacked into my computer after they were done when I got to my class the next day I found penutbutter on my keyboard and also I got alot of hard drive boot errror's ect after a while I go it going and then when xp boot's up I get a list of missing files I could tell they used some searching tool based on strings ect.

Well I have been messing with them for a while for payback becuse of that I was then only one they took the ip and mac adress of my computer now I plan at the end of this semister I plan to sell the computer.

The school itself are doing illegal activites like our state laws state's that during school hour's no none education advertising is allowed and yet on our daily annoucements on our school tv they had advertised some kid's rap cd ect and the prinicpal approved it even though that's an illegal activity.

So this school is not all innocent the staff they have their faviorit kids ect they play favorites and I am the only kid that has perfect attendance and I dont get respected at school like any other kid's
I usally used as labor like moving computers or any junk for the school to the main base where they have a storage house ect.

I am just planning to put a proxy up for those kids' in my class I know that I can't get introuble for doing that as long I don't use it.

People told me to use proxysquid with ssl so it can't be detected by the IT people.

---

