---
title: "Mouse-over/hover not working in VirtualBox Windows guest on 12.04 LTS host"
date: 2013-06-26
forum: Virtualisation
---

### Post by chrisjsmith on 2013-06-26
I've installed a 12.04 LTS host machine, installed virtualbox and have set up a Windows 7 x64 Pro guest (to run the last couple of apps I have to live with). Have installed vbox tools and the Oracle virtualbox extensions pack. Default hw accelerated Unity desktop.

It works pretty well bar one issue:

Typically when you hover over various things such as buttons, toolbars etc the mouse-over event isn't triggering inside the VM. I looked at it with Spy++ on Windows and there are no messages being delivered to the windows which suggests that virtualbox isn't sending the events. So no tooltips, no hovering actions, nothing.

Any ideas how to resolve this as it makes things rather hard when you need mouseover inside Visual Studio (which I still have to use while I port everything to Python)?

---

