---
title: "Two web servers on the same public ip. iRedMail running on a virtual machine."
date: 2015-09-22
forum: Server Platforms
---

### Post by alxhoff-d on 2015-09-22
Have been slowly setting up a personal server to move all cloud and email services i use onto my own server. I use owncloud as well as having phpvirtualbox hosted through the web server on a ubuntu server 14.04. Usually I test new packages or any major system changes on a virtual server before implementing them on the actual server but in this case I don't think I can.

I  was looking to install iRedMail on a ubuntu server 14.04 virtualbox . Being new to mail servers I decided to use a virtual machine as the iRedMail documentation states that it is intended to be used on a fresh server mainly to avoid any possibility of breaking any already installed packages.

The installation of iRedMail was a success and I can successfully send and receive emails through the server as I have forwarded the required SMTP port on my router to forward traffic to the virtual machines local ip. My biggest problem now is that the web interface used to read the mail goes through the virtual machines web server and I can only access it locally. Now my knowledge of ports and ip routing is good enough for a basic at home use but as I now find myself with two web servers needing to be addressable through the same public ip. I have done some reading on virtual hosting through ip-addresses but I am not sure if that is the right way to approach this problem.

I am wondering if there is a better way for me to handle all the various ports and subdomains on my web server rather than simply forwarding the ports on my router, maybe even a better way to set up iRedMail on the same server? something I need to implement from scratch so I can scrap my somewhat sketchy router set up?

I am after any wisdom or pointers from anyone with more knowledge on how to best handle this. Pointers towards packages or specific things I should google would be very helpful. 

Thank you in advance.

---

### Post by volkswagner on 2015-09-22
You have at least two choices.

A simple solution would be to use iRedMail web interface configured on port other than port 80, such as 8080 and/or 4443 vs 443.

Secondly you can setup a reverse proxy. You designate one server as main server which has port 80 forwarded from your router. Then setup
reverse proxy vhost files on this server pointing to alternate machines on your LAN. I have a basic tutorial [here]("http://ubuntuforums.org/showthread.php?t=1920715").

As mentioned in above thread, this is not to be used for HTTPS.

Hope this helps.

---

### Post by CharlesA on 2015-09-22
Assuming you can configure each of your services to use a separate sub domain, you could still run them off all the same IP and serving content over port 80 or 443.

This would likely need to be accomplished server-side, though.

---

### Post by TheFu on 2015-09-23
I use both methods above that Charles and volkswagner suggest above.

If you have wildcard DNS redirection (*.domain.org), then using name-based virtual hosts in the web server/reverse proxy is usually easiest. I must have 20 different web/app servers running here on the same IP, same port. It only becomes tricky when TLS is added - then you have to worry about client-side support for name-based TLS. Historically, 1 IP = 1 TLS cert. There are ways around that limitation now, if the client supports it. You shouldn't use SSL anymore - every SSL protocol has been compromised for 3+ yrs now.

The more important issue to me was the use of virtualbox for a "server".  It is heavier and slower than other alternatives.  In a real-world server deployment, NOBODY runs virtualbox. They use kvm or Xen - or a $12K/box commercial solution. Smaller shops might use proxmox.  Openstack is based on KVM, so I would strongly, advise using that - plus it is nice for server deployments and routinely the fastest virtualization hypervisor if you ever look at virt-spec numbers.

BTW - email really needs to be run inside a dedicated VM for security reasons. Email gets hacked all the time, not quite as much as wordpress, but enough to have it run on a different server install that you retain versioned backups for 120 days. 30 days hasn't been enough sometimes. People don't always realize when their servers are hacked within the first month.

IMHO.

---

### Post by CharlesA on 2015-09-23
> **TheFu said:**
> BTW - email really needs to be run inside a dedicated VM for security reasons. Email gets hacked all the time, not quite as much as wordpress, but enough to have it run on a different server install that you retain versioned backups for 120 days. 30 days hasn't been enough sometimes. People don't always realize when their servers are hacked within the first month.

Agreed on the email bit. That's part of the reason I decided to use hosted email instead of dealing with it myself. I [previously has it on its own VPS, but it was a bit of a hassle to manage it and deal with spam and whatnot.

Huge +1 on the versioned backups too. Without those, you would be up the creek without a paddle in the event your server got owned.

---

