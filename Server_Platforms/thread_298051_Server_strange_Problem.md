---
title: "Server strange Problem"
date: 2006-11-12
forum: Server Platforms
---

### Post by Star-x on 2006-11-12
Hi Guys Im new to server configurarion but thanks to great instalation instructions i did it perfect.
Now the problem: Instalation n problem. Installed joomla cms no problem register for free dns and was able to access my webpage using [www.mypage.freedns.com](www.mypage.freedns.com) in short everything was accessible ISPConfig worked excelent.

Then comes the day page not found connection refused on port 80.
and i could not access mail or ISPConfig.

then I login into the server as root and type "ping -w 60 google.com
after about 10 seconds from running this command everything was accessible as before and about 1 minute after the commandfinished then again no ISPConfig no access port 80.

I have no Idea what is creating such a problem please help

Cheers,

---

### Post by elst on 2006-11-12
It sounds like a problem with either the DNS servers or the network connection for the server.

I'm not really clear from your post where the server is located and how it connects to the Internet. Is this a computer on your own premises, or are you using a hosting service of some kind?

---

### Post by Star-x on 2006-11-12
First Thanks for reply 
Now let me clear it a bit more.

PC (Server is located at my home) ADSL Broadband Connection 512
I use service from [www.dyndns.com](www.dyndns.com) the free option there I created my domain name.
I follow (The perfect setup Ubuntu 6.06 LTS Server) and sucessfuly installed server with ISPConfig. Then I installed joomla CMS. 
Using ISPConfig I installed webmail. I also set up KMail and Evolution to read mail from the server. 
Once all has ben set up The server was up and running for a week. In that time I was able to access everything as you expect it to be. In short the server operated as it is expected from the server.

NOW PROBLEM 

Server was running Like before but it was not accessible only direct (Trough Monitor and Keyboard conected to it) or with (KSSH or PUTY)

Messages from browser were "Page not found"
Message when i check if my ISP is blocking port 80 was "connection refused your ISP does not block port 80" Tool used for this was from [http://www.dyndns.com/support/tools/openport.html](http://www.dyndns.com/support/tools/openport.html)

LOOKING FOR SOLUTION
I accessed server directly and tough to run PING command to see what will happen. You have to start somewhere and i dont know much about servers.

After running ping -w 60 google.com several times i found while the ping is running and about one min after it stops my server becomes accessible as it should be meaning( i can get my webpage, ISPConfig, Mail everything)

So I look into it and could not find anything strange since I always write down everything that i type when I do setups.

After the specified time the server enters sleep mode lets say It can not be accesible only direct.

I hope that this sounds much better sorry my first post was made at midnight.

Please HELP 

Cheers,
Star-X

---

### Post by elst on 2006-11-13
OK, I think that the problem is that your router or DSL connection is deactivating when it's not in use. This may be your router settings that automatically drop the connection after a period, or your ISP.

Once you start sending packets the connection is being reactivated and everything works until it deactivates again.

---

### Post by Star-x on 2006-11-13
Ok here is more details I had the server of line for one day and all the forwarded ports that I made active like 80, 81 etc I deactivate. Last night I Power on the server again and activate all the ports on my router. Check everything and it was working then I went to friends house check everything from there but just webmail. He does not have Evolution and Kmail just windows :) and everything was working.
I left the server on the whole night and today morning I check again and everything works.

Well as my little understanding about computer goes I know that they either work or they don't. And if they don't then you strat looking around for clues usually you find it and then you fix it and it works. But this is something that makes me go crazy and I have no Idea of where to look.

This is pure logic now if the router or ISP drops connection if inactive then how come it works today I even clear all the private data in my firefox and did Refresh + shift and all pages work ok.
Now everything works and I hope it will stay like this if it stops again I will post updates. 

Is it possible that someone could hack into it and just make it behave like this???? :confused: :confused: :confused: :confused:

---

### Post by Star-x on 2006-11-13
Thank you Elst for taking time and helping me I look into my router  to see if there is setting for this problem.

And another question IF the ISP blocks all this ports then how do they do it do they block them when they find them active and stop doing it when they become inactive. 

I'm new to this so sorry if I ask stupid questions.

---

