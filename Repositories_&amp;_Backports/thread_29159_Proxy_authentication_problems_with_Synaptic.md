---
title: "Proxy authentication problems with Synaptic"
date: 2005-04-23
forum: Repositories &amp; Backports
---

### Post by rjs on 2005-04-23
G'day all,

I'm having proxy authentication problems with Synaptic. I am unfortunatley behind a university proxy, so setting the proxy settings wasnt hard (simply changing them in preferences) but the network requires a username and password if you want to go outside the local network, and i cant see anyway of setting one (my university is sadly a micro$erf, so no hope of them having mirrors internaly, like ANU which is just a stones thorw away... ](*,)  but im getting diverted by my bitterness over not being at ANU, sorry). Anyway, any ideas on how i could set this this?

The error message im getting is 407 Proxy Authentication Required.

Hopefully,
rjs

---

### Post by rjs on 2005-04-24
Or if not in synaptic, then in aptitude? I dont even know how to set proxy config for aptitude, let alone proxy authentication settings, but if someone could point me it the right direction i would be very appreciative.

thanks,
rjs

---

### Post by mendicant on 2005-04-24
You want to add a file to /etc/apt/apt.conf.d:

% cat /etc/apt/apt.conf.d/01proxy
Acquire::http::Proxy "http://proxy.example.net:3128";
% 

For a user and password, make sure the file is read only root, and use (from the apt.conf(5) man page):

```

       http   HTTP URIs; http::Proxy is the default http proxy to use.  It  is
              in the standard form of [http://[](http://[)[user][:pass]@]host[:port]/. Per
              host  proxies  can  also  be  specified  by   using   the   form
              http::Proxy::<host>  with  the special keyword DIRECT meaning to
              use no proxies. The http_proxy environment variable  will  over&#8208;
              ride all settings.

```

---

### Post by rjs on 2005-05-10
ok, but how do i create a file in /etc/apt/apt.conf.d ? it tells me i dont have permition (even when im running from my admin account which has root privligages).

thanks,
rjs

---

### Post by mendicant on 2005-05-10
% sudo gedit /etc/apt/apt.conf.d/01proxy

Enter the Acquire line, and you should be good.  To test it, just run
% aptitude update

---

### Post by rjs on 2005-05-10
thanking you kindly good sir.

-rjs

---

### Post by mendicant on 2005-05-10
And that should be:

% sudo aptitude update

of course.

---

### Post by rjs on 2005-05-10
GGGGGGGGRRRRRRRRRRRRRRRRRRRRRRR!!!!!!!!!


i felt so pleased with myself when i edited the config file, to get the proxy working, then added the hoary-extra repositories. I was stumped for a little while, when i couldnt work out why i couldnt see gstreamer0.8-faac, but i thought about it and did an update, and it worked, and i installed it... but rhythmbox still friggin' doesnt play AACs. damn you apple, if it werent for your stupid iPods i could quite happily use oggs.

*rjs bangs his head against a wall*

ok, while i was poking around i installed gstreamer0.8 (this is before i installed gstreamer0.8-facc) and then uninstalled it. i can no longer find it anywhere, and im taking a wild guess that gstreamer0.8-faac wont work without gstreamer0.8 (since the former says it is a plugin for the later). How can i reinstall a package that i have deinstalled, and is this a reasonable assumption for what might be wrong.

thanks for your guidence up to this point, it really is much appreciated. Its nice just having updates, even without being able to use my iPod properly.

-rjs.

---

### Post by mendicant on 2005-05-10
[QUOTE=rjs]
ok, while i was poking around i installed gstreamer0.8 (this is before i installed gstreamer0.8-facc) and then uninstalled it. i can no longer find it anywhere, and im taking a wild guess that gstreamer0.8-faac wont work without gstreamer0.8 (since the former says it is a plugin for the later). How can i reinstall a package that i have deinstalled, and is this a reasonable assumption for what might be wrong.
[/QUOTE]

I tihnk you want totem-gstreamer.  I don't know what the command is in synaptic, but for aptitude:

% sudo aptitude install totem-gstreamer

The only other gstreamer packages I have are the plugins and the libraries.  You can search for what you might install using:

% aptitude search gstreamer ## no sudo needed here

---

### Post by rjs on 2005-05-10
nope,

it says totem-gstreamer is already installed. And when i did that search almost all gstreamer things had an i in front of them (which i presume means they are installed). what does capital A  mean when its infront of something in that list?

i might create a new post somewhere more relevent for this thread, since its not really  about repository support anymore.

thanks heaps,

-rjs

---

### Post by rjs on 2005-05-10
the prob was that i wanted faad not faac.
faac is for encoding not decoding.
yet another time when i should have READ THE FUCKING WIKI better.

thank heaps for your help.
-rjs

---

