---
title: "Two CUPS questions"
date: 2007-03-01
forum: Server Platforms
---

### Post by eziegler on 2007-03-01
Hello,

although cups is working quite well here, I have two problems that I'm not able to resolve:

(1) Cups found all the queues an icluded them with their correct name. At some point it decided to add the servername  with an "@" at the end of each queue (without changing any setting on client or server side) and does not recognize the normal queue names anymore (e.g. duplex@cups instead of duplex). This only happens on ubuntu machines.

(2) If a printer does not accept jobs for some time (e.g. due to a paper jam) it get's deactivated by cups and I have to restart the printer manually in the web interface. This is annoying because many users don't realize this issue and keep on submitting the same print jobs (yes, I should educate them better).

How can I deactivate this "features"?

Thanks,
    Emanuel

---

### Post by hlynur on 2007-03-06
I had the same problem .. as your problem nr 1. 
assuming you have 
BrowseShortNames Yes 
in your cupsd.conf I also had to comment out the server name 
#ServerName papir.domain.com
it is a bit weird but I dont know why it behaves like that if you have the ServerName declared.


after correcting cupsd.conf on the server and restarting cups there .. do sth like this on the client to clean everything up:

/etc/init.d/cupsys stop; sleep 1; killall cups-polld; rm /var/cache/cups/remote.cache; /etc/init.d/cupsys start

---

### Post by eziegler on 2007-03-06
Thanks, that solved the problem for now! I am not actually sure what the problem was and if it might appear again in the future.

I included "BrowseShortNames Yes" into the file although it should be enabled by default anyway.
Furthermore, I also commented the "ServerName" statement (which was set to the fully qualified host name and not its short version that was appended after the "@").

Still I have the feeling that deleting the cache files on the clients did most part of the trick, since undoing the changes mentioned above still gave short names. Once a wrong entry got into "/var/cache/cups/remote.cache", no broadcast or client restart seems to be able to correct the error.

I'll keep an eye on it and if the problem appears again, I'll try to figure out which particular setting solved the problem.

---

