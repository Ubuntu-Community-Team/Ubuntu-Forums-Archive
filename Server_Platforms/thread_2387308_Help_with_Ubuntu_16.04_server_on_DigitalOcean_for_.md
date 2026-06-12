---
title: "Help with Ubuntu 16.04 server on DigitalOcean for website hosting"
date: 2018-03-17
forum: Server Platforms
---

### Post by foomate on 2018-03-17
I was thinking about purchasing a droplet on DigitalOcean and create my own server instead of regular hosts like HostGator/GoDaddy etc..
And I wanted to consult with you about a few things:
1) Is it possible to get an Ubuntu server but as a GUI? (Like the desktop version?) Instead of a only terminal version? Because I would like to install softwares such as browsers to test my web and use PHPMyAdmin.
2) Security: If I follow their installation tutorials such as the one seen here: [https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04), Will my website be as secured as if I host on HostGator/GoDaddy? (I guess that they take care of security and that it's more "user friendly"?)

Because I feel like if I use their droplets, I basically have to take care of even the smallest issues I'd never think about. However it feels like I have more control of the website, that's why I am considering it. But again I feel like it might be bad security wise:
Assuming my website coding is OK (against SQL injections, XSS,etc..) - What will I have to take care about to prevent my server from being hacked, versus using a regular hosting service?

*I know since I am a beginner I'd probably be better off using regular hosting, but I'd like to learn as well :p

Thanks

---

### Post by TheFu on 2018-03-17
Cheap hosting seldom handles security well, if at all. Assume you need to do it if you want it done.  Hosting providers will leave you on the same version of everything until you decide to move to a newer version.  Non-working websites don't make paying customers happy, so they usually don't change anything proactively.  There are high-end hosting providers who do real security, but those are $100+/month.  On the cheap providers, expect all your neighbors to be bad guys. If only 10% are bad guys, you'll be more prepared.

I would assume that your website coding if flawed.  Secure coding is hard.  It takes years to hone that skill for each different language.  Follow all the **OWASP** checklists and code to the best of your ability. Stay current.  Stay patched. Avoid often-hacked tools.  Expect to be hacked and take precautions for what you will do *when* that happens.  I've been hacked 3 times, that I know. There might be instances where I didn't know about the hacks. Nobody is perfect.

> What will I have to take care about to prevent my server from being hacked, versus using a regular hosting service?  
There isn't any simple answer for that. A few general ideas: [http://blog.jdpfu.com/2016/10/04/lamp-server-security](http://blog.jdpfu.com/2016/10/04/lamp-server-security)  The specific answers you seek will depend on many things.  How much of a target you make?  How many attack vectors are left open, like web-based administration tools or remote GUIs? How quickly the system protects itself?  How long attacks are allowed to continue before shutting them down? How good the choice of tools are with making secure solutions?  How good the coding is? How much each service is locked down to only allow the users and systems which need access to have access while blocking everyone/everywhere else?
Every different sort of service has different attack vectors and different protection methods. Securing a DBMS server is different from securing a web server or reverse proxy server or email server.  Blocking access to any system that doesn't need to allow access is the first step.  Don't leave a DBMS open to the world if only the application server needs access.

You don't need to commit to either of the choices.  Why not try both a VPS and hosting?  After all, $5/month for a droplet isn't exactly a huge commitment.  You can spin up a VPS in 2 minutes, use it all day, then kill it off. If you pay by the minute or hour, that is a tiny amount of cash.  Do that a few times a week, when you have time.  Think on-demand, not all month.

As you know, there is a huge difference between "secure" and "working."   Linux/Unix is extremely flexible.  There are hundreds of thousands of settings that control almost every aspect of the server, a daemon, a service, and each subsystem. Time is needed to learn about each aspect. Security is hard.

How to start? By starting. Making mistakes. Recovering from those mistakes.  
[http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server) has my 1st Five Minutes on a new Server list.

---

### Post by foomate on 2018-03-19
Thanks, I ended up trying using it, it's really hard! But it's fun to learn, hope you can also answer some of those mistakes I already made (In my other posts :)  )

---

