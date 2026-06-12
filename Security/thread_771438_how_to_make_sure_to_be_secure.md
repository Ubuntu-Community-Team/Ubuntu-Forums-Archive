---
title: "how to make sure to be secure"
date: 2008-04-27
forum: Security
---

### Post by cmay on 2008-04-27
hi am to newbie to the whole internet thing to even begin think about what most of the words mean . i dont wanna get hacked that i do know. i run ubuntu and debian . i have posted a log from firestarter below. it is something completly new . i have nerver seen so many blocked attemts before. is my settings wrong or am i not hard enough to spot on the net. basically what i want to do is get the same secure default from ubuntu in every other distro . debian has some ports open by default how to shut them down or close them. 
in question of the internet i am puzzled whit everything  
sorry but the whole internet is full of words i dont understand it all sounds like starwars or black magic or something like that to me. 
it took me six month to open an email account simply becouse i dont see that well and i dont know anything whatsoever about how internet works. having just read two books we use in denmark for educational purpose for trainning programmers but i still dont understand it. i also read the book about minix by andrew s tannenbaum operative systems desing and implemetation. i learn c programmering right now . i learned pascal two years ago.
 i am not unaware of how an operative system works and what is inside it. i just cant figure this tcp/ip stuff out. 
its a miracle that i dont understand.

 can any one please help me be safe"re" on the net. thank you very much.

firestater blocks . are these hacking attempt or ?
Port:56424 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:14:30 Direction: Inbound In:eth0 Out: Port:56424 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:15:17 Direction: Inbound In:eth0 Out: Port:56425 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:14:30 Direction: Inbound In:eth0 Out: Port:56425 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:14:35 Direction: Inbound In:eth0 Out: Port:56421 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:14:36 Direction: Inbound In:eth0 Out: Port:56422 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:21:16 Direction: Inbound In:eth0 Out: Port: Source:213.178.69.122 Destination:80.165.172.103 Length:61 TOS:0x00 Protocol:ICMP Service:Unknown
Time:Apr 28 02:16:53 Direction: Inbound In:eth0 Out: Port:56425 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:20:59 Direction: Inbound In:eth0 Out: Port:42754 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:21:20 Direction: Inbound In:eth0 Out: Port:42754 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 02:24:08 Direction: Inbound In:eth0 Out: Port:42754 Source:91.189.94.186 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Unknown
Time:Apr 28 01:51:47 Direction: Inbound In:eth0 Out: Port:540 Source:4.79.142.206 Destination:80.165.172.103 Length:44 TOS:0x00 Protocol:TCP Service:Uucp

---

### Post by Chayak on 2008-04-27
To save me a lot of typing...
read the security sticky on top of the security area of the forum.

If your firewall is blocking it then it's not a problem.

---

### Post by cmay on 2008-04-28
never mind.
i have passed the test and i have whitout knowing anything at all
managed to get my system rated true stealht and the ports where all closed. so next time i wil just do the exackt same thing i did this time and pray that it helps.
thanks anyway.

---

### Post by Oldsoldier2003 on 2008-04-28
unless your server has a direct connection to the internet the stealth rating is for your router or gateway/modem. the whole online stealth thing is a bunch of alarmist BS coined by Gibson to drum up more business,

---

### Post by The Cog on 2008-04-28
Unless you are looking for something specific, you are better turning firewall logging off. Stuff it blocks isn't getting through so shouldn't worry you, and stuff that isn't blocked doesn't get logged. Now you know the firewall is actually dropping things, turn the log off and sleep easy.

---

### Post by cmay on 2008-04-28
hi again.
thanks for the replies.
i am looking for something very specific.
i had for some time a strong feeling i was craked on a previus ubuntu install. my own fault though. i went ahead and did the same as i did when using windows . install every thing from outside the repo. and pray it was not malware. thats along time ago however. 

but for some time after that i would have problems from time to time where things happen that i cant explain like when i was programmering and went out to get some coffe sit down and find that gcc would not be installed anymore. cheking and find that many files in the root && /usr/bin  directory was gone. stuff had permissions so i could not use the dvdburner and so on. 
i honestly dont know why but i installed freebsd for six weeks and after that i have had zero problems. the very first search i did on a linux distro was a distro called knoppix + mucix i think it was. the result was i got warnings from the firefox browser that this website was not who it claimed to be. it could be a malicius website searching for informations.
so i am always suspisius whit everything now. 

 i have followed an adwise and link given in the debian forum so thats the true stealht scan i refer to. there are open ports in debian by default and i wish i knew how to close them. besides that  i wanna learn this operative system and learn how to fix it when its brokne. i read all the things i can get about linux and minix and unix due to a problem i have whit being a very strict perfectionist and wanna always be an either expert or stay  unknowin/ unaware about things. so that means i bought for the sake of learning to use linux all the books from the danish training programs as datamatic 
( dont know if its the right word ?)
and to learn why software does not always work and why it works and to compare the software i learned pascal and now i try learn c as good as i can. just so i at least know these things.

my point is this simple. i dont have the energy to learn all there is to know in one quick go and i cant understand all of this internet yet. from htlm tags i can see on my own computer that its a html page but from there on i am lost for now. 
all the info i get from the stickie is great but i cant see a simple answer to how close ports so i dont have any open. thats all i need to know for now. i dont feel that good about askin these questions either since i know alot will think thyat its so basic that i must be stupid and should not have acces to an computer . 
and not a debian gnu linux since its not suitable for beginners. its just that i get medication for a disease that makes me very slow in my head /cancertreatment and i need to work whit something that just works for the simple demands as going to read mail. write an letter and print. and debian and ubuuntu does this better for me than windows did. i used to record whit cubase and sonar in a windows based computer studio set up but thats not the same as being on a linux machine whit acces to internet.

thanks for any pointers to the anwers if i can get any easy to follow step by step thing somewhere. 
searched on the debian homepage but its to big. 
any way thansk for reading this.

---

