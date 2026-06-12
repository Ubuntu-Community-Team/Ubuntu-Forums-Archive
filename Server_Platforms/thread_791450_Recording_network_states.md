---
title: "Recording network states"
date: 2008-05-12
forum: Server Platforms
---

### Post by cox377 on 2008-05-12
Hello All,

I'm running an ubuntu server, just for very basic stuff.

However some functionality I would like to have is to record all internet traffic coming onto the network, so having 2 Nics.. one connecting to the router and one connecting to the rest of the network.

I'm assuming in order to record traffic per IP etc it would have to act as a gateway opposed to just a pass through.

Any recommendations on how I would make a start on this would be grand.

CoXen

---

### Post by cdtech on 2008-05-13
Do you mean real time stats?

I use a few from the command line:

watch --interval=2 "sudo netstat -apn -l -A inet"
watch --interval=2 "sudo netstat -p -e --inet --numeric-hosts"
watch --interval=2 "sudo netstat -ano -l -A inet"
watch --interval=2 "sudo netstat -anp --inet --inet6"
watch --interval=2 "sudo netstat -tulpan"
sudo lsof -i
sudo netstat -tulpan

You could set something like this to log. I just use them when I need.

---

