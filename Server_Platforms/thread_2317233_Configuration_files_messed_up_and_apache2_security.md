---
title: "Configuration files messed up and apache2 security bypassed after ssh pipe broke"
date: 2016-03-14
forum: Server Platforms
---

### Post by rocknrocknroll on 2016-03-14
Hello all!

I have seen a strange behaviour, could you please give me hints of what I might have done wrong?

I am running ubuntu server 15.10 I have 2 websites runnning on apache2.

Let's say site1 ([www.site1.com]("http://www.site1.com")) and site2 ([www.site2.com]("http://www.site2.com")), with their respective conf files in /etc/apache2/sites-available (let's say site1.conf and site2.conf, with a virtual host in each)
These websites are very similar and the conf files are almost the same, just the servernames are different.
The 2 websites are supposed to have basic http authentication enabled so that they are not directly exposed to the internet.

Yesterday I logged in to my ubuntu server and the ssh pipe broke due to network error while I was editing a file (site1.conf). I was trying new directives and it is possible that I disabled basic http auth for site1 while doing so.

Today:
- I log back in my server and there is another file " .site1.conf.swp " in the sites-available directory.
- When I try to edit site1.conf with pico, I have an error message telling me the file is in use by nano
- I do something (I don't remember what sorry, I think I just exited pico, logout and login back to my ubuntu server), and the .site1.conf.swp file is gone and I can normally edit my site1.conf file

Now, here is where it gets very strange:

My basic http authentication on site1 is gone and the website is exposed to the internet. This might be due to a misconfiguration in site1.conf.
My site2 has basic authentication enabled and it works.

I remove site1.conf (rm site1.conf)
I copy site2.conf to site1.conf (cp site2.conf site1.conf)
I edit my new site1.conf to just change the folders and servername for my site1, nothing else.

But the http basic authentication is still not back in site1 !

Then, I copy: 
cp site1.conf test.conf.
en2dissite site1.conf
a2ensite test.conf

and the http basic authentication works for site1 (described by test.conf) !

site1.conf and test.conf have the exact same configuration options (just the path to the website and servername is different), but when site1.conf is enabled, http authentication does not work.
 When I move site1.conf to test.conf and enable test.conf instead, basic authentication work !!!

now that's scary to me, and I guess it has to do with the broken ssh pipe.. 
It is like the site1.conf file now refers to a "hidden" file somewhere in memory with basic auth disabled, that apache2 refers to.

Any clue?

PS: I do a sudo service apache2 reload every time I want to test the new conf

---

### Post by volkswagner on 2016-03-14
Perhaps you have a hidden file in /etc/apache2/sites-available

What is output of:
```
ls -al /etc/apache2/sites-available
```
and
```
ls -al /etc/apache2/sites-enabled
```

Please check logs for any helpful info.

You can use:
```
sudo service apache2 restart
```

---

