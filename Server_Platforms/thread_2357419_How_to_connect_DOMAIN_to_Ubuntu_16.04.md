---
title: "How to connect DOMAIN to Ubuntu 16.04"
date: 2017-04-02
forum: Server Platforms
---

### Post by jmoya4 on 2017-04-02
Just trying to follow some steps to point my domain, currently set up with Dreamhost, to my newly installed LAMP....Totally lost here...

---

### Post by cariboo on 2017-04-02
Moved to server platforms.

---

### Post by darkod on 2017-04-02
If you don't know dns basics, can something like this help you?
[https://www.digitalocean.com/community/tutorials/an-introduction-to-dns-terminology-components-and-concepts](https://www.digitalocean.com/community/tutorials/an-introduction-to-dns-terminology-components-and-concepts)

Note that you might not need to do much complicated records creation, in many cases you can use registrar/hosting company control panel to easily create records.

Depending on your case, the only thing you need might be to create A record with your registrar pointing to the public IP of your LAMP.

---

### Post by SeijiSensei on 2017-04-02
First, is the machine running the web server (presumably Apache) directly connected to the Internet, or is it behind a router, say on your home network?  

If the server has a public address, and you'd like it to respond to "www.example.com," then you need to add an "A" record to your nameserver configuration that looks like this:
```
www     IN     A     10.10.10.10
```
replacing 10.10.10.10 with the IP address of the public server.  Your provider probably offers a web interface for that task.  If your provider lets you specify "reverse DNS," then you'll also want to add a record that points 10.10.10.10 to "www.example.com".  You'll need to read the provider's documentation for that.

If you don't have a public server, things are much more complicated, so let's start with that first.

In addition, you'll want to create a configuration file for [www.example.com](www.example.com) in /etc/apache2/sites-available as described in [https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html).  I'd also name the computer "www" with the command "sudo hostname www" so it matches with its published name.

---

### Post by jmoya4 on 2017-04-03
Thanks for your responses. This is what I have...
enp03 inet addr: 192.168.0.23
lo  inet addr: 127.0.0.1

I am behind a router and currently have Apache installed..When I access the DreamHost panel domains DNS records, I'm not sure which of these IP addresses to use to point to my LAMP...

---

### Post by darkod on 2017-04-03
None of them... The 192.168.0.23 is a private IP assigned by your router. It is not reachable from the internet.

Does your router receive dynamic IP from your ISP? It is more difficult to do this with dynamic IPs. Also many ISP block incoming port 80 to prevent people hosting servers at home. If they do that in your case, you can't receive web traffic on standard port 80.

But to do a quick test, check your router public IP and use that IP in the dreamhost control panel to create A record.

Then on the router open port 80 in the firewall and forward it to 192.168.0.23. You do that with port forwarding options...

After that you should reach your apache website. But note that even if that works, if you public IP is dynamic the A record will no longer be correct after it changes.

---

### Post by SeijiSensei on 2017-04-03
To discover your IP address:  [https://www.whatismyip.com/](https://www.whatismyip.com/)

If this is a residential connection, there's a good chance that IP will change from time to time.  You'd also have to learn about "port forwarding" so that requests on the HTTP port, 80, are tunneled back through your router to your web server.

If this is more than just playing around as a hobbyist, you'd be much better off leasing a virtual machine in the cloud.  I pay $10/month each for a couple of machines at [Linode](http://www.linode.com/) though there are cheaper options out there.

---

### Post by jmoya4 on 2017-04-06
Cool! I appreciate your help. I was able to figure it out with what you all shared.....Thanks! =)

---

### Post by jmoya4 on 2017-04-06
> **jmoya4 said:**
> Cool! I appreciate your help. I was able to figure it out with what you all shared.....Thanks! =)

I appreciate everyone:Ds help. New to this forum, so, I haven't figured everything out just yet. Again, thanks!

---

