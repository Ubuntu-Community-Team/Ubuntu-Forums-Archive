---
title: "How should I go about this?"
date: 2007-09-03
forum: Server Platforms
---

### Post by nikomax on 2007-09-03
Hello Everyone!

Thanks to my school 6th form rules, I have to do some kind of community service (WOO lucky me... :|). 
So I decided before the summer that I would gather the lovely intellect of the lower school and revamp the terrible HTML of the schools Intranet site

So one of my plans is to create and Ubuntu server with LAMP And to be honest i really don't know what I'm doing. I know what i want to do though and I was wondering if anyone can help me with my plans.

One of the things that I wanted to do is the have a separate computer to run the web server, would it be better to use a Server Ubuntu installation or to use feisty?
It sounds obvious but i need something that is not too hard to set up and will integrate well with the schools set-up

Another thing is can I create internal domain names like ]www.ab12.com but get redirected internally to a server? Similar to a reverse NAT server.

Well i cant thing of anything else to ask at the moment. I have to discuss everything With my schools network manager. I have already been give a half go ahead but i need to submit detailed plans to him. and he doesn't like Linux so i will definitely have to know what im doing.
But i will also want to learn how to use server technology for a more personal use so and help and pointer will be great help Thanks

---

### Post by revford on 2007-09-03
Fiesty should be fine, just make sure you install the OpenSSH sshd so you can work on the machine remotely.

I don't know what you need to server to provide, if it's just web pages then you don't really need all of LAMP, you can dump the M and save a ton of config time.

You don't need the www. or the .com, if your school network has a DNS server of some kind, you can get the admin to add the hostname of your internal machine to it.

If you tell us what the machine has to host, I'm sure people can make more detailed recommendations.

---

### Post by nikomax on 2007-09-03
Sorry I didn't explain fully why I wanted LAMP. I was looking you use it to add a bit of dynamic content instead of constantly editing HTML. 
Teaching a learning with other students would be one of the most plus points of my project. I hopefully wanted to create some scripts to help the school student communicate better as it is terrible at the moment and no one is interested or  want to learn how.

The machine will host the web pages, scripts, Images, Flash content and maybe videos that have been approved by the school and any files that are work in progress will be there but separately kept .

I will look up abut OpenSSH and domain severs, but in the meantime do you have any links for me? 
:D

---

### Post by revford on 2007-09-03
On your local DNS, you'll have to speak to the network admin, only they will know how it's handled on your LAN.

As to OpenSSH, it's a modern replacement for telnet.  It's a way to open a terminal session from the server on your desktop, so you can enter commands and configure things without having to be sat at the server.  To install them try this:

```
sudo aptitude install openssh-server openssh-client
```

You can connect to the server either by hostname or IP address by opening a terminal and trying something like this:

```
ssh ADDRESS
```

Replacing ADDRESS with the host name or IP address of the server.  You can go ahead and run anything on the server from there, for example gedit to tweak the apache.conf file or adduser to accounts.

Have a look at the OpenSSH website for more basics:

[http://www.openssh.com/](http://www.openssh.com/)

---

