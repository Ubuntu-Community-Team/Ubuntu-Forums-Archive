---
title: "users running firefox from a tarball"
date: 2024-10-30
forum: Security
---

### Post by 1fallen on 2024-10-30
Security features warning

You may see a warning that &#8220;some of Firefox&#8217;s security features may offer less protection on your current operating system&#8221;.

The sandbox in Firefox makes use of unprivileged user namespaces when creating new processes for enforcing more security. This can be considered a security risk, therefore some Linux distributions have started to restrict its usage and only allow it to work where there is an AppArmor profile.

Such profiles can only cover a limited set of installations paths, including Snap and Debian packages. [U][B]They cannot however cover some other use cases, such as tarball installations as well as local development builds.
[/B][/U]
To create an AppArmor profile for Firefox:

In /etc/apparmor.d/, create a file with the name firefox-local

in the file, add the following:
```

# This profile allows everything and only exists to give the
# application a name instead of having the label "unconfined"
abi <abi/4.0>,
include <tunables/global>
profile firefox-local
/home/<USER>/bin/firefox/{firefox,firefox-bin,updater}
flags=(unconfined) {
    userns,
    # Site-specific additions and overrides. See local/README for details.
    include if exists <local/firefox>
}

```

**Replace <USER> with your Linux user name** This assumes the Firefox install is at $HOME/bin/

Once you have saved the file, run ```
sudo systemctl restart apparmor.service
``` in the terminal.


Share this article: [http://mzl.la/1xKrIV5](http://mzl.la/1xKrIV5)

---

### Post by ajgreeny on 2024-10-30
I am a little confused!

I have been running firefox from the direct downloaded .tar.bz archive from Mozilla for several years, ie since firefox became a snap by default, 20.04 was it? I can't remember!
However, I have always created a soft-link from the executable in that archive to /usr/bin/firefox and I run firefox simply using command firefox in a new launcher I created.

I admit that I don't and never have really understood apparmor but I wonder if the apparmor profile already in existence from the single run I made of the snap version before I removed it, ie, /etc/apparmor.d/firefox means I do not need this firefox-local profile or, as I have at the moment, do I need both **firefox** and **firefox-local** profiles?

---

### Post by 1fallen on 2024-10-30
I do both, I'm keen on security
ie:
```
sudo aa-status|grep firefox
[sudo] password for me: 
   firefox
   /usr/lib/firefox/firefox-bin (3547) firejail-default
   /usr/lib/firefox/firefox-bin (3666) firejail-default
   /usr/lib/firefox/firefox-bin (3668) firejail-default
   /usr/lib/firefox/firefox-bin (3721) firejail-default
   /usr/lib/firefox/firefox-bin (3823) firejail-default
   /usr/lib/firefox/firefox-bin (3915) firejail-default
   /usr/lib/firefox/firefox-bin (3960) firejail-default
   /usr/lib/firefox/firefox-bin (14548) firejail-default
   /usr/lib/firefox/firefox-bin (51303) firejail-default
   /usr/lib/firefox/firefox-bin (52329) firejail-default
   /usr/lib/firefox/firefox-bin (66050) firejail-default
   /usr/lib/firefox/firefox-bin (66205) firejail-default
   /usr/lib/firefox/firefox-bin (79894) firejail-default
   /usr/lib/firefox/firefox-bin (95285) firejail-default
   /usr/lib/firefox/firefox-bin (95482) firejail-default
   /usr/lib/firefox/firefox-bin (95563) firejail-default
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (132079) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (132235) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (132313) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (132443) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (132471) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (133110) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (133442) flatpak
   /home/me/.var/app/org.torproject.torbrowser-launcher/data/torbrowser/tbb/x86_64/tor-browser/Browser/firefox.real (133497) flatpak

```
I don't use the tarball method though, and I also had the snap firefox but you know me well enough to know that lasted about 15 mins....LOL

****[U][B]They cannot however cover some other use cases, such as tarball installations as well as local development builds.****

[/B][/U][U][B]I can however firejail the tarball with my install method

```
[/B][/U]sudo aa-status|grep firefox
[sudo] password for me: 
   firefox
   /usr/lib/firefox/firefox-bin (3547) firejail-default
   /usr/lib/firefox/firefox-bin (3666) firejail-default
   /usr/lib/firefox/firefox-bin (3668) firejail-default
   /usr/lib/firefox/firefox-bin (3721) firejail-default
   /usr/lib/firefox/firefox-bin (3823) firejail-default
   /usr/lib/firefox/firefox-bin (3915) firejail-default
   /usr/lib/firefox/firefox-bin (3960) firejail-default
   /usr/lib/firefox/firefox-bin (14548) firejail-default
   /usr/lib/firefox/firefox-bin (51303) firejail-default
   /usr/lib/firefox/firefox-bin (66205) firejail-default
   /usr/lib/firefox/firefox-bin (79894) firejail-default
   /usr/lib/firefox/firefox-bin (95285) firejail-default
   /usr/lib/firefox/firefox-bin (95482) firejail-default
   /usr/lib/firefox/firefox-bin (95563) firejail-default
   /usr/lib/firefox/firefox-bin (139254) firejail-default
   /usr/lib/firefox/firefox-bin (139349) firejail-default
   /opt/firefox/firefox-bin (146474) firejail-default
   /opt/firefox/firefox-bin (146551) firejail-default
   /opt/firefox/firefox-bin (146595) firejail-default
   /opt/firefox/firefox-bin (146624) firejail-default
   /opt/firefox/firefox-bin (146657) firejail-default
   /opt/firefox/firefox-bin (146742) firejail-default
   /opt/firefox/firefox-bin (146752) firejail-default
   /opt/firefox/firefox-bin (146782) firejail-default
   /opt/firefox/firefox-bin (146802) firejail-default


```

Both Firefox browsers was running the .deb and tarball

---

### Post by ajgreeny on 2024-10-30
Interesting!

The aa-status command at least shows both the firefox and firefox-local profiles are running.
```
~$ sudo aa-status|grep firefox
73:   firefox
74:   firefox-local

```
I will leave them as they are but would still be interested to know if both are really needed!

---

### Post by 1fallen on 2024-10-30
It's just a "little" more security is all.

And I know for a fact you use your browsers sensibly. (Common Sense)

---

### Post by 0f4d0335 on 2024-10-31
Nice find. Certainly you'd want to have an apparmor profile running. In the past Debian had one installed with its apparmor-profiles, but I've lost how to do it on Ubuntu. When you create an apparmor profile, you will need to tell the profile to conduct some behavior analysis and response. So I recommend using an established firefox profile over creating your own. I wonder if there's one maintained on GitHub that people recommend.

I just use snap because I can't stand to think about these things for too long. Far too boring. :biggrin:

---

