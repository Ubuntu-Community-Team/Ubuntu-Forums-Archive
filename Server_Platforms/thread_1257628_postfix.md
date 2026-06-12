---
title: "postfix"
date: 2009-09-04
forum: Server Platforms
---

### Post by pacco on 2009-09-04
i have googled seems like forever trying to find a fix this this problem,if im not clear please excuse me.

I registered a domain at dyndns.com,i want to setup postfix to send mail but it won't, i can 
recieve mail with no problem,could anyone help.

By the way all my ports are forward in my router

Here is the error:

[SIZE=1]2009/09/04 02:06[/SIZE] [SIZE=1]donald@smouselinux.com[/SIZE] [SIZE=1]donsmouse@frontiernet.net [/SIZE] [SIZE=1]592 bytes[/SIZE] [SIZE=1]connect to mx.frontiernet.net[66.133.129.79]:25: No route to host[/SIZE]


By the way i will include my master.cf file
Thanks In Advance

---

### Post by pacco on 2009-09-04
ok i just talked with my isp and they said that relay.frontiernet.net ?

So where do i put this at?

---

### Post by cariboo on 2009-09-05
A bump for the move.

---

### Post by pacco on 2009-09-05
i have tried everything,im just about to give up,but im not a quitter.
i entered relay.frontiernet.net in the reloayhost option in main cf and still nothing works
](*,)

---

### Post by cariboo on 2009-09-05
I'm not sure you will ever be able to send email with a dynamic ip address. Most mail servers do a reverse dns lookup, and if they don't recognize the ip address, all mail goes into a black hole. 

You may want to have a look at this [page]("http://fragments.turtlemeat.com/use-google-email-on-your-domain-name.php") to see if it will help solve your problem.

---

### Post by pacco on 2009-09-06
yeah i could get a private ip address from them,but that would cost a lot more,but thats how the make the money.

It kind of stinks,but maybe one day i will give them a call.

thanks for your help

---

### Post by pacco on 2009-09-06
actually i was wondering if i could just change my poert number from 25 to something else?

---

### Post by cariboo on 2009-09-06
The port number has nothing to do with it, it is your ip address that determines whether the email is sent on to its destination, or a black hole.

---

### Post by pacco on 2009-09-06
i remember that i had this setup before and it worked fine,but i can't remember how i did it
see my external address is 173.87.200.44 and my internal is 192.168.254.x,it shows that my port 25 is open and yes i know about the ip and port numbers,i just wish i could remember how i did it in the past

Here is the error i get in evolution:

The following message to <donald@smouselinux.com> was undeliverable.
The reason for the problem:
5.1.0 - Unknown address error 554-'5.4.0 Error: too many hops'

---

### Post by pacco on 2009-09-06
ok i got it to send mail this time,i uninstalled postfix,and installed exim4 now i cant send mail to my domain?

---

### Post by pacco on 2009-09-06
finally got it working,i just uninstalled postfix,dovecot and installed exim4 and courier-pop3,everything works like a charm,thank you all for your help.

---

