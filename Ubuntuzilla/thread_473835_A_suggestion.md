---
title: "A suggestion"
date: 2007-06-14
forum: Ubuntuzilla
---

### Post by FuturePilot on 2007-06-14
First let me give a [SIZE="5"]**BIG**[/SIZE] thanks to nanotube, aysiu, and anyone else who has contributed to the Ubuntuzilla script. I've used it many times on my Dapper installs and it always works flawlessly. 

Anyways this past time I had installed the [firefox-themes-ubuntu]("http://packages.ubuntu.com/dapper/web/firefox-themes-ubuntu") package from the repos. But after running the script the themes no longer showed up. Upon a closer look at the issue I found that the themes were installed to /usr/lib/firefox/extensions. I think the solution would be to symlink /usr/lib/firefox/extensions to /opt/firefox/extension in a similar way to the way the plugins are linked. I was just wondering if this could be implemented into the script?

---

### Post by nanotube on 2007-06-14
> **FuturePilot said:**
> First let me give a [SIZE="5"]**BIG**[/SIZE] thanks to nanotube, aysiu, and anyone else who has contributed to the Ubuntuzilla script. I've used it many times on my Dapper installs and it always works flawlessly. 

Anyways this past time I had installed the [firefox-themes-ubuntu]("http://packages.ubuntu.com/dapper/web/firefox-themes-ubuntu") package from the repos. But after running the script the themes no longer showed up. Upon a closer look at the issue I found that the themes were installed to /usr/lib/firefox/extensions. I think the solution would be to symlink /usr/lib/firefox/extensions to /opt/firefox/extension in a similar way to the way the plugins are linked. I was just wondering if this could be implemented into the script?

hmm, i will look into this. thanks a lot for your suggestion! will post back here with further thoughts soon. at first glance, sounds like a good point. :)

edit: hmm, indeed, it does seem like it would be a good idea to symlink to /usr/lib/firefox/extensions. i guess i will throw that into the next release of ubuntuzilla. thanks again for your feedback! :)

---

### Post by nanotube on 2007-06-14
oh by the way, did you try linking /opt/firefox/extensions to /usr/lib/firefox/extensions, and did the extensions work? im primarily concerned whether the "extensions" intended for f1.5 on dapper actually work for ff2.x? 
thanks ;)

---

### Post by FuturePilot on 2007-06-15
I haven't done that yet. But that's a good point. They might not work with Firefox 2.x. I will go try that and post my results.:)

Edit:
Well I got them to show up by symlinking the directories, but like you said, they weren't compatible. Sorry I totally forgot about that little compatibility thing:p:redface:

---

### Post by nanotube on 2007-06-15
> **FuturePilot said:**
> I haven't done that yet. But that's a good point. They might not work with Firefox 2.x. I will go try that and post my results.:)

Edit:
Well I got them to show up by symlinking the directories, but like you said, they weren't compatible. Sorry I totally forgot about that little compatibility thing:p:redface:

hehe no problem, it was a good thought, anyway. :)

---

