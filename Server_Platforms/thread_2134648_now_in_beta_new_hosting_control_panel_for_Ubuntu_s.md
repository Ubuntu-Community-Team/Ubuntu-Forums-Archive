---
title: "now in beta: new hosting control panel for Ubuntu servers"
date: 2013-04-11
forum: Server Platforms
---

### Post by FreedomCP on 2013-04-11
Hi all,

We've just launched the beta of our free hosting control panel, FreedomCP.

[https://freedomcp.com](https://freedomcp.com)

How it works is that you connect an Ubuntu server to us (by installing our agent), then you manage your server through our web interface. Currently, you can configure PHP and Python applications and MySQL databases. We setup nginx as the public-facing webserver on your server. PHP apps are run through FPM, Python apps through gunicorn. For PHP apps, nginx proxies to Apache first so that your apps can use .htaccess files.

Our goal is to make FreedomCP the easiest way to configure and manage your servers and web applications.

We're just getting started and are looking both for feedback on our beta as well as suggestions on what features you'd like to see.

Thanks,
Justin

---

