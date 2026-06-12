---
title: "Using Ubuntu server"
date: 2017-07-24
forum: Server Platforms
---

### Post by RobGoss on 2017-07-24
Hello everyone, I was wondering if someone could help me out with a question about using Ubuntu server for hosting my own personal website

Can I setup Ubuntu on a extra machine I have here at home and use it to host a personal blog of mine using Ubuntu server 

There's not a lot of traffic so it won't use that much resources 

I would also like to use my own domain with the new server is it hard to setup, I would also like to know would I be able to use WordPress with this home server as well

I've seen a lot of videos on setting things up but I don't know is it really worth all the trouble 

I normally use Chanel with WordPress so I don't know how that would work having a home server

I know there's a lot of details that go into doing things like this but I'm willing to learn if it will be better then using a online hosting service

Thanks so much for any help with this

---

### Post by mastablasta on 2017-07-24
> **RobGoss said:**
> 

Can I setup Ubuntu on a extra machine I have here at home and use it to host a personal blog of mine?

There's not a lot of traffic so it won't use that much resources 
[/QUOTE]
Yes.
> 
 I would also like to use my own domain with the new server, I would also like to know would I be able to use WordPress with this home server 

Thanks so much for any help with this

yes on both. though domain has to be registered outside at domain registrars (e.g. at godaddy, hostgator etc.).

install server, install LAMP and openSSH, then install wordpress, secure the server, get domain and set it all up. open server to internet and you are good to go.

though if you don't have much trafic it might be cheaper&easier to just create a blog at worpdress.com or blogger

---

### Post by RobGoss on 2017-07-24
Thanks for the fast reply, WordPress.com and Blogger are Free services and not very good as far as features, they limit the use of the WordPress editor 

I currently use Hostgator but would like to learn how to setup a home server . I tough having so many machines I could use one for a home server. I've never setup one so this would be all new to me

I already have my domains for a few years now and I host them with Godaddy

Thanks for any information you can provide for this

---

### Post by SeijiSensei on 2017-07-24
Before you go too far down this road, make sure your ISP isn't blocking inbound traffic to port 80.  I'd install Ubuntu server, start Apache, and set up port forwarding on the router.  Then from an external client, try to view the default Apache web page by browsing to your external IP address.  If it shows up, then you're good to go.

---

### Post by RobGoss on 2017-07-24
>   before you go too far down this road, make sure your ISP isn't blocking inbound traffic to port 80    

Why would this be blocked? Is it because of my Internet provider, is this something they do?

---

### Post by btindie on 2017-07-24
Another issue you may have is to do with your IP address. Generally home users would get a dynamic IP address meaning that it can change at anytime.

If it's not going to have much traffic then this may not be much of an issue.

You could always use a service such as [https://www.noip.com/](https://www.noip.com/) to manage the dynamic IP address. You'd run a client ( Ubuntu package inadyn ) on your server that periodically updates it with them. And in your own DNS you'd create a CNAME record to point to the no-ip.com record. So if your IP address changes, the IP address associated with your domain would also get updated.

Depending on your router, that may already support DDNS.

See also [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

---

### Post by RobGoss on 2017-07-24
> **btindie said:**
> Another issue you may have is to do with your IP address. Generally home users would get a dynamic IP address meaning that it can change at anytime.

If it's not going to have much traffic then this may not be much of an issue.

You could always use a service such as [https://www.noip.com/](https://www.noip.com/) to manage the dynamic IP address. You'd run a client ( Ubuntu package inadyn ) on your server that periodically updates it with them. And in your own DNS you'd create a CNAME record to point to the no-ip.com record. So if your IP address changes, the IP address associated with your domain would also get updated.

Depending on your router, that may already support DDNS.

See also [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

The router I have is provided by my Internet provider so as far as changing anything I'm not sure if I'm allowed to or even can

---

### Post by wildmanne39 on 2017-07-24
*Thread moved to **Server Platforms**.*

---

### Post by dragonfly41 on 2017-07-24
Try installing ngrok on your home server .. and you can choose the port ..

[https://ngrok.com/faq#self-hosting](https://ngrok.com/faq#self-hosting)

You will have an ngrok address but from your domain you can direct to this.

I have an account with google domains and they provide a convenient one stop interface which can be used with (separate) google cloud account.
Google cloud provides some limited free hosting.

---

### Post by QIII on 2017-07-24
Most ISPs block port 80 on residential accounts.  To be able to set up a website, a more expensive business account is required.  To echo previous advice:  you should check with your provider before going down this road.

---

### Post by mastablasta on 2017-07-25
security of the server itself will be your main preoccupation as well as setting up backups.

as for the router - usually you are allowed to do changes and open ports, but like others said port 80 (used on apache) may be blocked and IP may be dynamic with no option of static one.  

where i live they also use dynamic but the way they use it is a bit strange - it is same IP address only marked as dynamic. so every day at midnight it owuld do the switching but actually stay the same after the switch, and so most host here do not have an issue with changing this into static IP. 

they also do not have any ports blocked. although the business account does offer quite a bit more. and i guess they would notice if traffic was too large.

in any case for website hosting i prefer to have it handled by professional host. things are then much easier when any issues arise. and they probably will.

our home server is used and aimed at maximum 10 clients concurrently, although it never happened. additionally it is locked down quite a bit. even so there are daily attacks and probing logged against it.

---

