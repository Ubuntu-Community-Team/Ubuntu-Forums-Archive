---
title: "has anybody been able to install the Firefox 4 authentication key?"
date: 2011-03-27
forum: Security
---

### Post by nrundy on 2011-03-27
I have been unable to access the key file since installing Firefox 4 Tuesday. I have no authentication key for Firefox.

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x0AB215679C571D1C8325275B9BDB3D89CE49EC21&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x0AB215679C571D1C8325275B9BDB3D89CE49EC21&op=index)

---

### Post by oldos2er on 2011-03-28
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x9BDB3D89CE49EC21](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x9BDB3D89CE49EC21)

Copy that entire text to a local file, for example mozilla.ppa.key. Run **sudo apt-key add mozilla.ppa.key** in a terminal.

---

### Post by nrundy on 2011-03-28
so I open Gedit, open webpage, select all, copy, and then paste into Gedit, then save to hdd?

---

### Post by Soul-Sing on 2011-03-28
> **nrundy said:**
> so I open Gedit, open webpage, select all, copy, and then paste into Gedit, then save to hdd?

No it has to be "pushed" through the ubuntu keyserver via the terminal.

: [http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/](http://www.omgubuntu.co.uk/2011/03/firefox-4-ppa-for-ubuntu-10-04-and-10-10-users/)
and the key is visible in the softwaresources: system: administration: softwaresources: keys.

---

