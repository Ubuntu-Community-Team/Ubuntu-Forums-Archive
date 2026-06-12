---
title: "Redirect specfic Apache requests"
date: 2011-12-12
forum: Server Platforms
---

### Post by chrislynch8 on 2011-12-12
Hi,

I have a rewrite rule directing traffic over HTTPS if it does not come from my internal LAN. I want to alter this to do the following.

I want everything redirected except for three requests i.e.

website.com -> redirect
website.com/index.php?entry=tracker -> do not redirect over https
website.com/index.php?entry=tracker2 -> do not redirect over https
website.com/index.php?entry=tracker3 -> do not redirect over https

At the moment I am using thef following to redirect

RewriteEngine On
RewriteCond %{HTTP_HOST} ^\website.\com$
RewriteCond %{REMOTE_ADDR} !^10.10.10*$
RewriteRule (.*) https://website.com$1

How would I include conditions to not rewrite the three example above

Rgds
Chris

---

