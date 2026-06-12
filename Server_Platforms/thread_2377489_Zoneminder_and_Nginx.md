---
title: "Zoneminder and Nginx"
date: 2017-11-14
forum: Server Platforms
---

### Post by databoy2k on 2017-11-14
Another clueless question; needing more help from the gurus.

I'm trying to install Zoneminder. I've already installed software that uses Nginx, and so of course I'm running into the issues associated with Nginx and Apache on the same server. 

I'm following this site to install zoneminder into nginx: [https://chiralsoftware.com/idea/nginx-ubuntu-and-zoneminder](https://chiralsoftware.com/idea/nginx-ubuntu-and-zoneminder)

I'm stuck at the part about creating the zm-include file. I've created /etc/nginx/zm-include using the snippet provided, but I don't understand the part about "include the above in the appropriate server definition."

Can anyone spare a few minutes to educate an Nginx-neophyte in what that means?

Thanks.

---

### Post by databoy2k on 2017-11-14
Alright mods 24 hours of Re-Education (Through Labour) means you can close this.

For anyone who stumbles onto the closed thread, follow the readme here to use the provided nginx.conf file: [https://github.com/ZoneMinder/ZoneMinder/tree/master/distros/ubuntu1604](https://github.com/ZoneMinder/ZoneMinder/tree/master/distros/ubuntu1604)

Also, as of writing, make sure you update the reference to php7.0 to php7.1. 

(To the sound of a heartbeat pounding away...)

---

