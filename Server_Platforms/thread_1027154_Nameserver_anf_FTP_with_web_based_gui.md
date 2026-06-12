---
title: "Nameserver anf FTP with web based gui"
date: 2009-01-01
forum: Server Platforms
---

### Post by PC_Nerd on 2009-01-01
Hi,

I'm starting to setup my own server, and I wanted to get some advice on packages to install regarding FTP and nameservers.  I understand that there are GUI's available for most of these applications - but I have a terminal only access ( though is it possible to run X11 on a seperate machine and setup gui through that or something?).

I wanted to be able to do as much of the configuration as possible through a web interface... I understand that I would probably need to install apache etc to do so and thats not a problem.

Thanks for any advice,
PC_Nerd

---

### Post by windependence on 2009-01-01
As with most people, you have probably been led to believe that you need to run your own nameservers to run a web site. You absoluetly don't need to. Use your registrar's nameservers or your ISP may also allow you to use theirs. Setting up your own DNS is a bear, and if you don't need to do it, I wouldn't.

As to the other stuff, why so scared of the CLI? Almost all configuration files in Linux are just plain text files. You don't have to use VI as the text editor either. Nano, is a good, easy to use command line editor and will have you going very quickly. My advice ( I know you won't like it) learn the CLI and you will be happy you did. What would happen if you fancy GUI or web interface took a crap after you spend hours setting up your stuff? It would be a shame to have to recreate all that stuff when you could fix it in a few minutes from an ssh session.

-Tim

---

### Post by PC_Nerd on 2009-01-01
Hi,

I think I've probably approached this from the wrong direction.  Firstly I'm not under the misconception of running my own namesevers.  I've been using my hosting companies for over 2 years now.  I've recently upgraded to a VPS, and I wanted to start hosting everything myself ( mainly as a learning thing).

As for the CLI etc, I'm most definatly not afraid of it etc, Ive recently manually configured/compiled: php, apache, mysql and iptables as my firewall all through a SSH and using nano.

The reason im asking for recomendations etc on a web based interface is that I wanted to save time instead of having to edit files - I can simply login through a web browser etc....  So is it possible etc?

* on an unrelated matter but in passing, does anyone know much about ubuntu 8.04 and vsftpd... ssl-cert is required, but it failes ebcause it cant find a key (make-ssl-cert generate-default-snakeoil).... however to make that it needs ssl-cert.... weird.... ( just in passing for anyone who has used it, if I have issues later on ill post it elsewhere (yes I know this is the wrong place)).

Thanks

---

### Post by /carlito on 2009-01-02
you should propably google for webmin...

---

### Post by PC_Nerd on 2009-01-02
ok, thanks

---

