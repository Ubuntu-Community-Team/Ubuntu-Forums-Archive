---
title: "nginx user and permissions"
date: 2010-06-02
forum: Server Platforms
---

### Post by goneskiing on 2010-06-02
installed nginx with sudo apt-get install nginx

trying to deploy with node.js with nginx and having a terrible time - the /etc/nginx/nginx.conf shows:

user: www-data

does that mean nginx is running as user www-data ?  we don't have such a user, does it need to be added ?  

we are running node.js with a "node" user we created -and all app files hae a node user as owner.

---

### Post by arrrghhh on 2010-06-02
www-data user I believe is created when apache is installed... do you have apache installed?

---

