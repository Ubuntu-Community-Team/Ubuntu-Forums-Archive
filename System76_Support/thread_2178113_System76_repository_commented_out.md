---
title: "System76 repository commented out"
date: 2013-10-01
forum: System76 Support
---

### Post by Newbunto on 2013-10-01
My laptop came with Ubuntu 11.10 and then I let it upgrade to Ubuntu  12.04 LTS and I notice now, many months later, that the relevant line in  [FONT=courier new]/etc/apt/sources.list.d/system76.list[/FONT] has been commented out with the  comment "disabled on upgrade to precise". Is that badness? Is there  something that I should be doing with that? If so, what are the  commands? Do I just edit the file in order to uncomment?

---

### Post by houstonbofh on 2013-10-03
This is normal Ubuntu upgrade behavior.  All 3rd part repos are commented out during upgrade.  You have to go in manually, and change them to the correct version (Precise) and re-enable them.

To fix use "Software Sources" under edit in the Software Center, under Repositories in Synaptic or by running "sudo software-properties-gtk" in a terminal.  Or you can manually edit it, and to an "apt-get update" after.

---

### Post by isantop on 2013-10-03
What the line say? Does it have "planet76.com" in it, or "ppa.launchpad.net"?

---

### Post by Newbunto on 2013-10-03
> What the line say? Does it have "planet76.com" in it, or "ppa.launchpad.net"?

[FONT=courier new]deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./[/FONT]

was the line before commenting out.

Apart from uncommenting it out, do I need to change it as well?

Edit: Forum is stuffing up the format but hopefully clear enough.

---

### Post by isantop on 2013-10-04
Nope, that's the correct line for 12.10 and earlier. You should be good to simply uncomment it.

---

### Post by Newbunto on 2013-11-08
What's the correct System76 repository for Ubuntu 13.10 then?

---

### Post by isantop on 2013-11-08
The correct way to add the repository on 13.04 and later is by running this command:

```
sudo add-apt-repository ppa:system76-dev/stable
```

Ubuntu will automatically expand this command into the correct format, and add an entry to your sources.list.d directory.

---

