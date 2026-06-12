---
title: "How do I make Apache2 start at boot? Ubuntu-server 16.04LTS"
date: 2016-09-13
forum: Server Platforms
---

### Post by wh33t on 2016-09-13
I'm also curious why this isn't the default behaviour. It used to be. 

Thanks :D

---

### Post by cariboo on 2016-09-14
On all my server installs, apache starts automatically. You could try:

```
sudo systemctl enable apache2.service
```

then

```
sudo systemctl start apache2.service
```

---

### Post by wh33t on 2016-09-14
> **cariboo said:**
> On all my server installs, apache starts automatically. You could try:

```
sudo systemctl enable apache2.service
```

then

```
sudo systemctl start apache2.service
```

Have you done any 16.04LTS Ubuntu-Server installs lately? I would like to know why mine doesn't auto start. 

So doing the "enable" somehow registers it as a system start up service or something?

---

### Post by cariboo on 2016-09-14
The last 16.04 install I did was early last week, in a vm, but that shouldn't matter. I'd suggest you run the following command to see if there is a problem with your configuration.

```
sudo apache2ctl configtest
```

to see if there is a problem with your configuration that may stop apache from starting automatically.

Yes 

```
systemctl enable apache2.service
```

registers the service to start automatically.

---

### Post by wh33t2 on 2016-09-14
> **cariboo said:**
> The last 16.04 install I did was early last week, in a vm, but that shouldn't matter. I'd suggest you run the following command to see if there is a problem with your configuration.

```
sudo apache2ctl configtest
```

to see if there is a problem with your configuration that may stop apache from starting automatically.

Yes 

```
systemctl enable apache2.service
```

registers the service to start automatically.

Awesome. Thank you.

---

