---
title: "Port forwarding"
date: 2011-02-11
forum: Server Platforms
---

### Post by sramm9 on 2011-02-11
Hai

Dear All
Hope someone could help me.
a) currently to access my webserver from internet i need to type in the below format:->
---> [http://epbt.dyndns.tv:10080/](http://epbt.dyndns.tv:10080/)    

But , i would actually want it in this format:-> [http://epbt.dyndns.tv](http://epbt.dyndns.tv)   ONLY. without having to type the port#

My webserver is running on Apache.

Via Fortigate Firewall, i already did the mapping of "Source Port= 80' ---> map to local ip = 10080.

Please advice on how i can do this?
Thank you so much....
.d

---

### Post by elico on 2011-02-11
well i am accessing an apache server with tomcat on 
[http://epbt.dyndns.tv/](http://epbt.dyndns.tv/)
so it's working.

---

### Post by sramm9 on 2011-02-12
Hai

Dear Elico,

Thanks for the reply.
I am new to this. My development team has done the program and now face this problem of not able to hide the port number.

see attached file , please:

a) Yes typing as i mentioned previously gives the Tomcat screen.
b) But the actual url is : " [http://epbt.dyndns.tv:10080/epma_mbjb/](http://epbt.dyndns.tv:10080/epma_mbjb/) "
c) how can i hide the port#? , 10080
d) my screen attachment shows , what i have done on the firewall and the screen for this URL

please advice
thank you so much
.d

---

### Post by elico on 2011-02-12
now i do understand the problem.
and it's not a problem.

you have one ip address that you connect to using the domain
epbt.dyndns.tv
the epbt.dyndns.tv points now to the ip address 203.121.38.8
the http protocol is using default port 80
which means when you use the line [http://epbt.dyndns.tv/](http://epbt.dyndns.tv/)
the browser trying to connect the ip 203.121.38.8 on port 80
and the line [http://epbt.dyndns.tv:10080](http://epbt.dyndns.tv:10080) means your browser will try to connect 
ip 203.121.38.8 on port 10080

your firewall setup is ok for what you get and if you do want to make it use  [http://epbt.dyndns.tv/](http://epbt.dyndns.tv/)
you should change you firewall settings to
not 10080 to 80 but 80 to 80
and all will be fine.

but there is another rule there that doing port mapping from port 80 to to other server so you might want to erase this rule or change it.

regards Elico

---

### Post by sramm9 on 2011-02-12
Hai

Dear Elico

Thanks for the reply.
Yes , it works now.
Thanks a million.

For my extra knowledge, can u explain what u mean by the last statement?

--> " but there is another rule there that doing port mapping from 80 to to other server so you may want to erase this rule or change it "
---------------------------------------------------------------------------------------------------

Also, the initial url is meant for the public to access.
So for developers/programmers accessing different folders , i could use the same url with addition of '\........  something ,,, thats all rite?

Pls advice
thank you so much .
.d

---

### Post by elico on 2011-02-12
well i dont know your network and firewall structure but if i got tomcat apache page it means that im accessing some server and it could be the result of other rules that already exist on this firewall that points port 80 to 80 or the local firewall web-server page.

about the developers you can build anything you want let sat directory named "dev"
and you can access it using the url
[http://epbt.dyndns.tv/dev](http://epbt.dyndns.tv/dev)

just out of curiosity what is this site about?

---

### Post by sramm9 on 2011-02-13
Hai

Thanks again..
This site is a portal for public to access data related to city council
tq so much 
.d

---

