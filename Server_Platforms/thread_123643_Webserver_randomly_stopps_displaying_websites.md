---
title: "Webserver randomly stopps displaying websites"
date: 2006-01-30
forum: Server Platforms
---

### Post by OneSeventeen on 2006-01-30
Every once in a while my ubuntu webserver will stop displaying the websites hosted on it.

It will work perfectly fine for a few weeks, then just stop responding.  I just type in 
/etc/init.d/apache2 restart
and it reloads just fine and works as though nothing ever went wrong.

When it is down, I can still ping all of the URL's successfully, and I can ssh into the server using any of the URLs or any of the IP addresses assigned to it.

It feels like an apache problem to me, but I'm not quite sure.  Any tips on how I can track this issue down?

---

### Post by Horndog on 2006-01-30
Look in your Apache error logs for a clue.

---

### Post by OneSeventeen on 2006-02-03
It looks like it is reaching it's MaxConnections limit.

What are acceptable maximum connections, and what exactly constitutes a connection?

If I just waited it out, would I get a response from the server after a while, or does it completely shut down?

If it just blocks me until a connection opens up, does me restarting the apache server block other's connections and free one up for me?  (if so... oops)

I'm just glad this isn't 100% production yet!

---

### Post by Horndog on 2006-02-03
If you post the ***[color=red]relevant[/color]*** parts of the log maybe some one can help you adjust the MaxClients  setting to allow more traffic.

---

