---
title: "Custom Apache Log"
date: 2011-07-06
forum: Server Platforms
---

### Post by securitymeddler on 2011-07-06
Hey guys, 



  First off I am new to web server support. I have a request from my management to modify the logging slightly. 



  Effectively I need to redirect a custom string from our http response into the apache access logs. 
  

When a user navigates to our site they receive a “dye” number that is associated with them. This number follows them to whatever cluster they are directed too. The string is formatted as such , com-company-dye: d0a2#6dfce. 
  

I need that that header dye to appear in the access logs so we can use that dye number as a key for troubleshooting issues though out our various monitoring systems. 



If there is a better forum I should post to, please direct me.

---

### Post by SeijiSensei on 2011-07-06
If the number doesn't appear as a parameter in the URL, you won't be able to trace it.  If the URI is something like /index.php?dye=12234, then you'll see that in the access log.

Without knowing more about the application you're using, it's hard to figure out how to help.  If, for instance, you're using PHP, you could add some code that runs each time a page is accessed that writes the dye number to a log that the application itself maintains.

---

### Post by securitymeddler on 2011-07-06
That is what I asked too. But code modification is out of the question. 

Ideally I was hoping there was a module or .config I could modify that would just snag the entire headers out. It would be easier for me to filter after the fact and deal with a couple more gigs of data a day than it would be to get even a single line of code added. 

Think I am out of luck?

---

### Post by ruffEdgz on 2011-07-06
Well, I don't know about being out of luck but it will take a little of reading of apache docs and understanding if 'com-company-dye' value is being passed from the browser to the server in a cookie or HTTP request and response headers.

I would look at these websites from apache about custom logs:

[http://httpd.apache.org/docs/2.0/mod/mod_log_config.html](http://httpd.apache.org/docs/2.0/mod/mod_log_config.html)

In the 'custom log format' section, I would look at seeing if [%...{Foobar}i] or [%...{Foobar}C] can help you get the correct information you need to be logged into a custom log file.

This would be an **example** of how to use the above as a custom log:
```

CustomLog logs/custom_access_log "%h %l %u %t \"%{com-company-dye}C\"

```
or
```

CustomLog logs/custom_access_log "%h %l %u %t \"%{com-company-dye}i\"

```

You will need to find out if either/or options above can be done and if the variable is called something else. I used a tool like [Live HTTP Headers](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/) to help me get the correct information if you wanted to know.

Cheers!

---

