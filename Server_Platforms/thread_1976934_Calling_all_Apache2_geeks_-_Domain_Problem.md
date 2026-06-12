---
title: "Calling all Apache2 geeks - Domain Problem"
date: 2012-05-09
forum: Server Platforms
---

### Post by coffee412 on 2012-05-09
First a big hardy thank you for reading my post!

I have registered a domain name at godaddy and run a home server with ubuntu-server 12.04 / Apache2. I have everything working fine but seem to have a problem with the display of my domain in browsers.

Browsers display my ip address instead of my actual domain name. I have tried to talk to godaddy about this but they are really not all that helpful. They just point me to articles on how to edit A records ect... 

My problem is that I dont know if this is a config error in apache, a domain config error ? 

I have tried redirecting my domain with masking on godaddy but that has not done anything. Waited a whole day to make sure. 

Kinda frustrated at this point. I type in my domain name in the browser and it changes to the ip address. Connecting to webserver is fine and dandy. Its just this stupid ip address showing instead of my *.com domain name.

I sure would appreciate some help here. 

coffee:confused:

---

### Post by SeijiSensei on 2012-05-09
The only way I can think of that this would happen is if you're using a Redirect of some kind.  Suppose you have the domain [www.example.com](www.example.com) and you define a Redirect for it in Apache like this:

```

<VirtualHost *:80>
     ServerName  www.example.com
     Redirect    /  http://10.10.10.10/
</VirtualHost>

```

Then requests for [www.example.com](www.example.com) will be redirected to the IP address 10.10.10.10, and that address will be used in the browser's address bar.

You might also get this result if you use a RewriteRule of some kind that rewrites URLs with alphameric domain names to IP addresses.

---

### Post by coffee412 on 2012-05-09
Thanks for your reply,

Finally got this worked out. Wouldnt you know it, Right after posting about it I got the problem fixed. Geez.. 

The DNS record at godaddy's had an extra @ line in there. I got rid of that. Cancelled the redirect at GDs,Then I emptied my cache.

Thanks for taking the time though to reply. We be done!

Here is my website so far if you are interested:

[http://www.renuecomputers.com](http://www.renuecomputers.com)

---

