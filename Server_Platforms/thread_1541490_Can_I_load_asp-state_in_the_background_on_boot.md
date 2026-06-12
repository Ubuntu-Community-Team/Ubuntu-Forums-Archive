---
title: "Can I load asp-state in the background on boot?"
date: 2010-07-29
forum: Server Platforms
---

### Post by dugald on 2010-07-29
Hi all,

I have finally set up my mono/apache server to persist session state info using the asp-state element of the xsp server package.

I have to start it manually once I have booted the server using a "asp-state" command from the shell.  It then starts reporting all events in the shell and has a "press enter to exit" line at the bottom.

I really need this to start automatically on bootup.  I have tried adding it to bootup actions in Webmin (it is added as a service) but although it starts, it seems to effectively halt the loading of other services that should have started after it as it is just sitting there reporting events and inviting me to press enter.  Is there any way to have it run properly in the background?

Thanks for any advice.

---

