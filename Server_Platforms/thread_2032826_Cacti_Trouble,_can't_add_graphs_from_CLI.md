---
title: "Cacti Trouble, can't add graphs from CLI"
date: 2012-07-24
forum: Server Platforms
---

### Post by derelict888 on 2012-07-24
I've recently installed cacti using repos and then added a web page speed test tool from this website; [http://www.askaboutphp.com/44/cacti-using-cacti-to-monitor-web-page-loading-part-1.html]("http://www.askaboutphp.com/44/cacti-using-cacti-to-monitor-web-page-loading-part-1.html")

After following the guide above I have setup templates so I can add a bunch of websites via CLI for monitoring. Trouble is its not working. Drilling down I have found that Cacti thinks there is no input field for the graph template;

```
# php -q /usr/share/cacti/cli/add_graphs.php --graph-template-id=47 --list-input-fields
Known Input Fields:(name, default, description)
*[no results]*

```

I have copied all these templates from a working version of cacti on an older install of buntu/cacti;
```
~# php /usr/share/cacti/site/cli/add_graphs.php --graph-template-id=37 --list-input-fields
Known Input Fields:(name, default, description)
50:url          URL
```

I can't see any difference in any of the templates with the exception of names I've used. Anyone have any ideas?

(the template IDs are correct)

---

### Post by Habitual on 2012-07-25
Seen this?
[http://www.cacti.net/downloads/docs/html/cli_add_graphs.html](http://www.cacti.net/downloads/docs/html/cli_add_graphs.html)

---

### Post by derelict888 on 2012-07-25
> **Habitual said:**
> Seen this?
[http://www.cacti.net/downloads/docs/html/cli_add_graphs.html](http://www.cacti.net/downloads/docs/html/cli_add_graphs.html)

Yes thanks for the reply though.

---

### Post by derelict888 on 2012-07-25
I'm moving this to Cacti's forum, here is the thread I started there: [http://forums.cacti.net/viewtopic.php?f=12&t=47934](http://forums.cacti.net/viewtopic.php?f=12&t=47934)

---

