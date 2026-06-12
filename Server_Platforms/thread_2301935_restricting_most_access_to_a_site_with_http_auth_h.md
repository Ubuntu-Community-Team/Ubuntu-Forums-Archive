---
title: "restricting most access to a site with http auth haproxy"
date: 2015-11-06
forum: Server Platforms
---

### Post by Matt_Davies on 2015-11-06
Hi everyone

I've just started digging into haproxy today, and so far, so good.

I've restricted access to a site, with http basic auth, but my next hurdle is to restrict all access, apart from a couple of URL's on the site.(API's access them and adding http auth to those would be a pain)

So, lets say the web site is called ilovemydogsomuchithurts.com, and the following code is restricting access, how would I change the code to NOT restrict access to ilovemydogsomuchithurts.com/kennelupdates.json and ilovemydogsomuchithurts.com/puppyupdates.json?

I'm seeing some reference to url_reg, but can't quite work out how to accomplish this.

Any tips, or links to docs would be very much appreciated.

```
userlist UsersFor_kennel
  user username insecure-password password
  
frontend doghttps
  bind public_ip:443 ssl crt /etc/ssl/private/dog.crt
  reqadd X-Forwarded-Proto:\ https
  default_backend dog


frontend doghttp
  bind public_ip:80
  reqadd X-Forwarded-Proto:\ http
  default_backend dog


backend dog
  acl AuthOkay_kennel http_auth(UsersFor_kennel)
  http-request auth realm kennel if !AuthOkay_kennel
  redirect scheme https if !{ ssl_fc }
  server 1-www private_ip:80 check
  server 2-www private_ip:80 check

```

---

### Post by sandyd on 2015-11-07
> **Matt_Davies said:**
> Hi everyone

I've just started digging into haproxy today, and so far, so good.

I've restricted access to a site, with http basic auth, but my next hurdle is to restrict all access, apart from a couple of URL's on the site.(API's access them and adding http auth to those would be a pain)

So, lets say the web site is called ilovemydogsomuchithurts.com, and the following code is restricting access, how would I change the code to NOT restrict access to ilovemydogsomuchithurts.com/kennelupdates.json and ilovemydogsomuchithurts.com/puppyupdates.json?

I'm seeing some reference to url_reg, but can't quite work out how to accomplish this.

Any tips, or links to docs would be very much appreciated.

```
userlist UsersFor_kennel
  user username insecure-password password
  
frontend doghttps
  bind public_ip:443 ssl crt /etc/ssl/private/dog.crt
  reqadd X-Forwarded-Proto:\ https
  default_backend dog


frontend doghttp
  bind public_ip:80
  reqadd X-Forwarded-Proto:\ http
  default_backend dog


backend dog
  acl AuthOkay_kennel http_auth(UsersFor_kennel)
  http-request auth realm kennel if !AuthOkay_kennel
  redirect scheme https if !{ ssl_fc }
  server 1-www private_ip:80 check
  server 2-www private_ip:80 check

```
Create two backends, one with http-request auth, and one with no http-reqeust auth.

Now, you can use ACLs in the frontend to redirect some requests to a non-passworded backend.

Example (not tested):
```

userlist UsersFor_kennel
  user username insecure-password password
  
frontend doghttps
  bind public_ip:443 ssl crt /etc/ssl/private/dog.crt
  reqadd X-Forwarded-Proto:\ https
  acl is_noauth url_beg  /kennelupdates.json
  acl is_noauth url_beg /puppyupdates.json
  acl is_existingdomain hdr(host) -i ilovemydogsomuchithurts.com
  use_backend doghttp-noauth if is_noauth is_existingdomain
  default_backend dog


frontend doghttp
  bind public_ip:80
  reqadd X-Forwarded-Proto:\ http
  acl is_noauth url_beg  /kennelupdates.json
  acl is_noauth url_beg /puppyupdates.json
  acl is_existingdomain hdr(host) -i ilovemydogsomuchithurts.com
  use_backend doghttp-noauth if is_noauth is_existingdomain
  default_backend dog


backend dog
  acl AuthOkay_kennel http_auth(UsersFor_kennel)
  http-request auth realm kennel if !AuthOkay_kennel
  redirect scheme https if !{ ssl_fc }
  server 1-www private_ip:80 check
  server 2-www private_ip:80 check

backend dog-noauth
  redirect scheme https if !{ ssl_fc }
  server 1-www private_ip:80 check
  server 2-www private_ip:80 check

```

---

### Post by Matt_Davies on 2015-11-09
Hi Sandyd

Thanks for getting back to me

Nearly worked, just a small problem I think, probably syntax

I get this

error detected while parsing switching rule : no such ACL : 'AND'.

from these types of lines

use_backend doghttp-noauth if is_noauth AND is_existingdomain

searching for the answer now

---

### Post by Matt_Davies on 2015-11-09
ok, if I comment out the acl is_existingdomain lines, and just use 

use_backend doghttp-noauth if is_noauth

that seems to work

Am I removing something important by taking out the acl is_existingdomain lines?

Thanks again Sandy

---

### Post by sandyd on 2015-11-09
Try without the word "AND"

The third ACL, i.e.
```

acl is_existingdomain hdr(host) -i ilovemydogsomuchithurts.com
```
prevents domains that are not ilovemydogsomuchithurts.com from triggering the path matches

---

### Post by Matt_Davies on 2015-11-10
Thanks Sandy, that worked a treat.

I was wondering how I was going to split out different sites coming into haproxy, as I bind on the IP address.

Is this the preferred method of splitting out what to do with different urls, as opposed to binding on a URL?

```
acl is_existingdomain hdr_beg(host) -i URL
```

---

### Post by sandyd on 2015-11-10
It is the preferred way to match a ACL condition via domains (i.e. hosts).

Once the ACL is matched (this one is called is_existingdomain), you can use them in conditions such as
```

use_backend doghttp-noauth if is_noauth is_existingdomain
``` to select which backend you want to push request through.

Now that I look at it again - spotted another error.

hdr_beg is for matching the beginning of a domain, not the exact domain.

I've updated the example above to reflect.

Sorry about that.

---

### Post by Matt_Davies on 2015-11-12
Thanks Sandy, your help has been invaluable!!

Matt

---

