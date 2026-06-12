---
title: "DHCP &amp; Defining new options"
date: 2010-06-07
forum: Server Platforms
---

### Post by niceee on 2010-06-07
Hello,

I set up a dhcp server thanks to dhcp3-server on an ubuntu 10.04. I am trying to create new options. I tried what is said in man dhcp-options. Namely, i tried to add following lines in dhcpd.conf :

[I]option myoption code 194 = text;
option myoption "HELLO";
I rebooted dhcp3-server after modifications. But new options aren't sent. I sniffed datagramms thanks to wireshark but the new options don't appear in dhcp request.


Have you got any ideas to solve this problem ?

Regards

PS : Sorry for my poor english.
[/I]

---

### Post by niceee on 2010-06-07
up:(

---

### Post by arrrghhh on 2010-06-07
What are you trying to achieve?  I don't get why you're adding those 'options' at all...

---

### Post by niceee on 2010-06-08
I would like to send some pieces of information which arent in the DHCP standard to clients.

[I]option myoption code 194 = text;
option myoption "HELLO";

should works
[/I]

---

### Post by arrrghhh on 2010-06-08
Ok, I can't help you then.  Those lines are meaningless, I don't understand why you would want to send those to a computer... Are you trying to send something useful like SLP info or something?!?

---

### Post by niceee on 2010-06-08
Thank you for your answer.
Actually it is for a student project and it doesnt concern  some options which are implemented in DHCP standard. I have to define new ones. It could be usefull in any case, for example to send another IP address than those which are in the standard.

[I]option newipaddress code 194 = ip-address;
option newipaddress 192.168.1.1;[/I]

But defined options arent sent either with these lines.

It might be possible according to  dhcp-options man :
[http://linux.die.net/man/5/dhcp-options](http://linux.die.net/man/5/dhcp-options)
( heading "Defining new options" )

---

### Post by arrrghhh on 2010-06-08
Ah, I am sorry... I cannot provide assistance for a school project - you gotta learn the stuff man!

Even if I could, I'm not sure how.  I've only implemented a standard dhcp server, nothing fancy.  Honestly these forums are not for homework help - kinda defeats the purpose.

---

### Post by pedro_orange on 2010-06-08
Presumably you'd need something something that could consume the options, otherwise they would be ignored. You might have to run some sort of custom application that could see the arguments you're passing it.

---

### Post by koenn on 2010-06-08
maybe the protocol requires that clients request options to make the server send them ? Or maybe you have to configure the server to actually 'force' these options on the clients ? 
don't remember exactly, you may have to read up on the dhcp protocol

or maybge it's just a syntax issue, i.e. that you didn't set up those custom options correctly. Maybe they're in a wrong sectopn f the conf file ?

---

### Post by WinstonChurchill on 2010-06-09
If your clients are using Linux, it would seem to me you could ask for these "options" in the request clause of /etc/dhcp3/dhclient.conf - the manpages seem to imply that this is supported, but if your clients aren't running Linux you're probably screwed. There seems to be no way to "force" an option on a client.

---

### Post by niceee on 2010-06-10
thx for your  answers, i'll get back to you!

---

### Post by Iowan on 2010-06-10
From CoC:> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.For what it's worth - so far, the thread seems to be within the "hints and ... questions when you get stuck and need a little help". :)

---

### Post by niceee on 2010-06-27
Hey,

I solved my problem. I was trying to catch options with a PC on windows so it didnt work.
I tried with a Linux PC and after a little modification in /etc/dhcp3/dhclient.conf on the client side, i noticed that my new options was sent !
However, i dont know how to catch it. 
It must be done since **/sbin/dhclient-script **, variables are called with '$new_OptionName'.
 e.g. : **$new_ip_address**. 
It works with dhcp standard options. But I don't manage to catch the value of  my defined option.
Any ideas ?

---

### Post by koenn on 2010-06-28
maybe
[http://manpages.ubuntu.com/manpages/lucid/en/man8/dhclient-script.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/dhclient-script.8.html)
and look at "hooks"

---

### Post by niceee on 2010-06-28
Thx for ur reply koenn.
I looked at /etc/dhcp3/dhclient-exit-hooks.d/debug
As it's written in this script, by setting a value on 'yes' we can see different variable used in /sbin/dhcp-script. but my defined option didnt appeared, i got following lines : 

> Mon Jun 28 22:42:47 CEST 2010: entering dhclient-enter-hooks.d, dumping variables.
reason='REBOOT'
interface='eth0'
medium=''
alias_ip_address=''
new_ip_address='192.168.2.60'
new_subnet_mask='255.255.255.0'
new_domain_name='test.org'
new_domain_search=''
new_domain_name_servers=''
new_routers='192.168.2.254'
new_static_routes=''
old_ip_address=''
old_subnet_mask=''
old_domain_name=''
old_domain_search=''
old_domain_name_servers=''
old_routers=''
old_static_routes=''
--------------------------
Mon Jun 28 22:42:47 CEST 2010: entering dhclient-exit-hooks.d, dumping variables.
reason='REBOOT'
interface='eth0'
medium=''
alias_ip_address=''
new_ip_address='192.168.2.60'
new_subnet_mask='255.255.255.0'
new_domain_name='test.org'
new_domain_search=''
new_domain_name_servers=''
new_routers='192.168.2.254'
new_static_routes=''
old_ip_address=''
old_subnet_mask=''
old_domain_name=''
old_domain_search=''
old_domain_name_servers=''
old_routers=''
old_static_routes=''
-------------------------However, my client ask for my created option as we can see on the fllwing screenshot : 
[LEFT][IMG]http://img138.imageshack.us/img138/5197/listeoptions.png[/IMG]
[/LEFT]

Then, the server send that option : 

[IMG]http://img265.imageshack.us/img265/5784/definedoption.png[/IMG]

it tallies with what i defined, namely an option called **myoption** with **code 194** and a text content : **"helloworld"**

I obviously use some casual values for the test. 

I'm close to get what I want, i just need the name of the variable for my defined option ?

---

### Post by koenn on 2010-06-28
well, it looks as if you can have a dhcp server  effectively send out custom options. So the *will* arrive at the client, seeing that they are part of the dhcp packet's payload.

To do something useful with it, the dhcp client should capture that value in a way that other programs can reference it, or in a way that the dhcpclient itself can pass it on to the rest of the system.

I assume the dhcp client hooks are entry points where you can get access to such a value, or exit points that let you pull up that value. But that's as far as it goes for me. I've set up a few servers with "user-defined" dhcp options, but only to accomodate client software that already expected an option of a given type/number/... 

So how you get a client to use that option, I don't know. However, in the man page there's some talk about how dhcp client hooks are used to  transfer the option "DNS server" to /etc/resolv.conf. If you find where and how that's done, you can probably use a similar mechanism to transfer the value of your option to a file, or pipe it to another program, and there you are, then.

---

### Post by niceee on 2010-06-28
all right thx.

>  However, in the man page there's some talk about how dhcp client hooks  are used to  transfer the option "DNS server" to /etc/resolv.conf. If  you find where and how that's done, you can probably use a similar  mechanism to transfer the value of your option to a file, or pipe it to  another program, and there you are, then.

If someone know about such a mechanism, please tell me.

---

### Post by koenn on 2010-06-29
I read some man pages .
Maybe you should do the same


```
man 5  dhcp-options
man 5 dhclient.conf
less /sbin/dhclient-script 
man dhclient-script
```

here's an idea:
you can define dhcp options in the client conf as well. So if you define an option with the same number and datatype as you did on that server, possibly the client will assign the received value to a variable with the name of that option. Presumably, you can then call that var from one of the client/hook scripts, or something along those lines.

---

### Post by niceee on 2010-06-29
That's what i did, but it doesnt work.
And i m fed up with manpages ^^

---

### Post by niceee on 2010-07-03
up

---

### Post by niceee on 2010-07-06
up

---

