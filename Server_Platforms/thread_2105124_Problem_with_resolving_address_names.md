---
title: "Problem with resolving address names"
date: 2013-01-15
forum: Server Platforms
---

### Post by viktorjano on 2013-01-15
Hello!

I have a problem with connecting my server to internet and therefore I can not install any new updates, desktop environment and so on. 

It is very unusual that the first time I have installed the server it managed to connect to the Internet and started downloading from repositories. But due to a low disk space it ended with a fatal error, without bringing the job to the end. Than I repartiotioned the HDD, making some more room for the server itself, but after that the connection to the Internet is impossible. I was fiddling around a bit. First added manually the gateway address, and after that it managed to connect. After that it appeared problem "cannot resolve address ...", which meant it couldn't resolve the address of the repositories. Than I added manually address of a known DNS which I can ping, but the problem with the resolving stayed. One possible problem is that, as it says in the commented part of the *resolv.conf* file, it is automattically rewritten after closing it. So maybe a possible solution to the problem is to find way how to force DNS server address to my server, in other words **how to edit the *resolv.conf *file without beeing rewritten**?

---

### Post by viktorjano on 2013-01-15
Guys I found the culprit, no need to waste mental resources!!! It was an internal router in the network with an ip address that made the conflict. After changing its ip address everything is ok... it was very unusual coincidence!!!

Thanx anyway

---

