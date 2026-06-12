---
title: "Need eBox and Webmin Help"
date: 2009-02-13
forum: Server Platforms
---

### Post by deejross on 2009-02-13
I have a Ubuntu server which needs to act as a gateway for the network + proxy + content filter + firewall. I have already set this up using eBox. The problem was that eBox doesn't let me modify the settings I need access to (ones that are in config files, but not in eBox). So I have been editing the config files for squid and dansgaurdian. I also used eBox's firewall module to block access from outside to the inside network. I have it configured exactly the way I need it for now.

HERE'S THE PROBLEM: I can't make any changes in eBox now without it asking me to overwrite all the changes I've made. So I'd rather use Webmin so I don't have to walk on eggshells to make changes without screwing up all the configuration. The thing is, Webmin seems to think there is no firewall. So is there a way to remove eBox without screwing up anything and use Webmin to manage everything and take over the firewall configuration?

I went into to all of this thinking that eBox was the answer to system management, but it turns out that Webmin was...and still is. Yes, eBox it make the initial set up easy, but using it to manage the system is a nightmare if you need to manually edit something that eBox doesn't have a GUI for.

Help with this would be greatly appreciated.

---

