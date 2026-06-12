---
title: "SSH tunnel automization"
date: 2008-03-27
forum: Security Discussions
---

### Post by thefatmoop on 2008-03-27
So my college takes the liberty of blocking anything that may have "adult, porn, security, foreign, programming, hacking, viral" on websites, and they're required to log everyone's visited urls... This college is ridiculous (transferring next year to a state school) 

Anyway i have an ssh tunnel proxy at home and it gets bothersome to type 

```
 
ssh -D port client@host
client@host password: 

``` 

I don't want my computers to automatically establish the connection

is there a way to just make an icon that would do it? the account is non administrative so i don't care if the password is stored on the comps. or a plugin for firefox that will login and redirect firefox?

---

### Post by thefatmoop on 2008-03-27
bump

---

### Post by HermanAB on 2008-03-27
First install a public key on your server so you don't need to type a password, then simply make a desktop thingy using Nautilus or Konqueror (right click).

---

### Post by thefatmoop on 2008-03-27
yea i haven't done that yet.. .could anyone access it then?

---

### Post by HermanAB on 2008-03-27
A public system consists of a key pair, private and public.  You keep the private key on your machine in your room and put the public key on the machine at home.  Then , when you log in with ssh, it will use the two keys to authenticate you without any further user input.  For this to be secure, your private key has to remain private.

---

### Post by FakeOutdoorsman on 2008-03-27
For the Firefox side of things:
Look into the [SwitchProxy]("https://addons.mozilla.org/en-US/firefox/addon/125") or [FoxyProxy]("http://foxyproxy.mozdev.org/") extensions.  These will allow you to configure your proxy settings and easily switch between the proxies.  I prefer the simpler SwitchProxy, but FoxyProxy will also allow you to use a certain proxy per site.

If the school also filters by the site name (via DNS requests) you should use a non-school related DNS server or use a remote DNS server through a proxy.  I believe you can configure FoxyProxy to use remote DNS requests through the ssh tunneled computer.

If you have a router at home that is capable of using third-party firmware such as DD-WRT, then it can act as your proxy since it is always on and uses less power than a standard computer:
[How can I secure my computer when using public wifi?]("http://ubuntuforums.org/showthread.php?t=712919&page=2") (See posts #12 and below).

---

### Post by honeydew on 2008-03-28
> **thefatmoop said:**
> So my college takes the liberty of blocking anything that may have "adult, porn, security, foreign, programming, hacking, viral" on websites, and they're required to log everyone's visited urls... This college is ridiculous (transferring next year to a state school) 

Anyway i have an ssh tunnel proxy at home and it gets bothersome to type 

```
 
ssh -D port client@host
client@host password: 

``` 

I don't want my computers to automatically establish the connection

is there a way to just make an icon that would do it? the account is non administrative so i don't care if the password is stored on the comps. or a plugin for firefox that will login and redirect firefox?


Right click the top panel.. choose add to panel and then custom-launcher-icon and create name etc etc.. for command do  
```

gnome-terminal -x ssh -D port client@host

```

then proceed with creating a public private key... on the terminal type
```

ssh-keygen

```
when it asks you to enter a password.. just hit enter(dont type anything). copy your /home/user/.ssh/id_rsa.pub  to [email]client@host:/home/user/.ssh[/email]/authorized_keys this could be done with

```

scp .ssh/id_rsa.pub [email]client@host:.ssh[/email]/authorized_keys

```


once that is done you should be able to click the icon and have it automaticly forward ports through your server(with no password).. there maybe a way todo this with out gnome-terminal.. but it may be kinda nice having the window so you knew the status of your connection.  on a side note it may be nice to have some type of integration like this into the gnome network manager.  Kinda like the VPN connection tools..

be well!

---

