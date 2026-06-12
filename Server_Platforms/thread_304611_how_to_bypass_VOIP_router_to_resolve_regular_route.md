---
title: "how to bypass VOIP router to resolve regular router?"
date: 2006-11-22
forum: Server Platforms
---

### Post by Eaglejazz on 2006-11-22
I am currently running Ubuntu Server 6.06

Everything was going planned as scheduled when setting up hosting my own domain but arrived at problem i am currently trying to figure out.

Ill tell you the process I went thru:

First i registered my domain. Then i had to configure the nameservers via  [www.zoneedit.com]("http://www.zoneedit.com") / (also zoneclient for Dynamic IP update) and directed to apache on router with virtual servers running a SMC router.

But thats when the problem comes into play, i went to my domain and found a dlink VOIP login, where i should have found my content on the apache server. So i asked my buddy to go to site and he said problem connecting to server. So now i am wondering on how to bypass my VOIP router to read my regular router so that it can direct it to apache via virtual server. Then everything can work. 

If you have any soltions to this problem you can be a truly a blessing.

Thanks Eaglejazz

---

### Post by rickyjones on 2006-11-22
OK - Let me try to map this out and see if it jives with how you currently have it set up.

```

*******************
    Internet
*******************
           |
           |
       |-------|
       | SMC  | (First router)
       |-------|
           |
           |
       |-------|
       | VOIP | (VOIP router)
       |-------|
           |
           |
       |-------|
       | LAN   | (LAN + Webserver)
       |-------|

```

This is what I think is happening. You might have two routers: The first is an SMC router where you did the initial port forwarding. The other is VOIP router. If so, you might need to just move the server from the before-stated LAN, to the SMC LAN side. Of course, more information is going to be needed to really figure out /what/ is going on.

Hope this helps!

---

### Post by Eaglejazz on 2006-11-22
Actually the setup is a bit different:

```


#######################
         Internet
#######################
             |
          (MODEM)
             |
 _____________________________
 | (VOIP Router) - DLINK 1120|
 |___________________________|
             |
             |
  _________________________
  | SMC Router  ADSL router|
  |________________________|
              |
              |
       __________________
       |LAN / WEB Server|
       |________________|
      


```

Hope that helps. I also tried, leaving the VOIP router out of the equation but once i did that the internet didnt work so it is configured to read VOIP router. Anyways thanks for continued help!

Eaglejazz

---

### Post by MJN on 2006-11-23
Your Dlink router is listening on port 80 and hence answering to requests on it. I'm not familiar with its config however you should look to either disabling it listening altogether on port 80 or changing the port it listens to to something else).

Alternatively you can change the port that Apache is listening on however this is undesirable given that's the port it's meant/expected to be listening on.

That aside, you mentioned configuring your SMC router to forward port 80 to your server, however you didn't mention doing likewise on the D-Link? If you haven't done this you need to, otherwise it won't know where to send port 80 traffic to.

Mathew

---

### Post by Eaglejazz on 2006-11-26
I found the answer on Dlink site regarding VOIP routers, mine was the Dlink 1120M through PRIMUS. Here's the link...[http://support.dlink.ca/faq/view.asp?prod_id=2298&question=DVG-1120M]("http://http://support.dlink.ca/faq/view.asp?prod_id=2298&question=DVG-1120M")

So what it is saying here is conect the VOIP router behind the current SMC router in the diagram below like so...
[CENTER]
```
          #######################
                 Internet 
          #######################
                     |
                  (MODEM)
                     |
         ______________________________________________________
         | SMC Router  ADSL router|. --------->  | Voip Router | 
         |________________________|  --------->  | Dlink 1120M |
         
              |                     
              |
              __________________
              |LAN / WEB Server|
              |________________|
```
[/CENTER]


As you can see that the Voip service uses a lan line and ig you log on to your router and look under status of the DHCP Client Log you'll it has added your VOIP router in there.

Hopefully this is helpful as this solvedmy problem. Now all you have to do is configure FTP and WEB server and you are in business

Eaglejazz

Thanks for all those whom tried to help!

---

### Post by Eaglejazz on 2006-11-26
Sorry try this link...other one was in further just click on VOIP behind router.

[http://support.dlink.ca/products/view.asp?productid=DVG%2D1120M]("http://support.dlink.ca/products/view.asp?productid=DVG%2D1120M")

Eaglejazz

---

