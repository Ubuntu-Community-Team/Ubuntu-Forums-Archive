---
title: "Nginx server"
date: 2020-08-14
forum: Server Platforms
---

### Post by ssk1234 on 2020-08-14
Issues setting up .htpasswd and redirect from www to secure https site.

I have set up the following in the conf file. However, htpasswd and only the www to secure non-www are not working (all other redirects to the SSL site) are working. 

When it comes to the htpasswd, I have no issue with htpasswd for Apache. This issue is only with Nginx.

    listen 80;
    listen [::]:80;

    server_name [www.####.com](www.####.com) ####.com;
    #server_name [www.####.com;](www.####.com;)   

    location / {

       #return 301 https://$server_name$request_uri;
       #return 301 $scheme://####.com$request_uri;

       auth_basic "Restricted Content";
       auth_basic_user_file "/etc/nginx/.htpasswd";
       #return 301 $scheme://####.com$request_uri;   

    }

    if ($host = ####.com) {
        return 301 https://$host$request_uri;
    } 

    #if ($host = [www.####.com](www.####.com)) {
    #    return 301 https://####.com$request_uri;
    #} 

    if ($host ~ ^[^.]+\.####\.com$) {
        return 301 https://$host$request_uri;
    } 

Any suggestions would be appreciated. ](*,):roll:

---

### Post by ssk1234 on 2020-08-17
May I know whether there is any connection between Ubuntu forums and this one? [https://www.explorelinux.com/server-nginx-server/](https://www.explorelinux.com/server-nginx-server/)

I did not post here and noticed the same content over here.

---

### Post by coffeecat on 2020-08-17
> **ssk1234 said:**
> 
I did not post here

Yes you did. Or at least, someone who has access to your Ubuntu One SSO account, and therefore the ssk1234 ubuntuforums account, did. If it was someone with access to your account, they were also posting from the same IP address as the address you just posted from now. Occam's razor suggests therefore that it was you that posted the first post to this thread. Or do you have an alternative explanation?

---

