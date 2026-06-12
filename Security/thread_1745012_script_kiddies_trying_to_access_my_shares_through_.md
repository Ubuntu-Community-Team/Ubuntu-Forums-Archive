---
title: "script kiddies trying to access my shares through apache2"
date: 2011-04-30
forum: Security
---

### Post by Blond_Knight on 2011-04-30
Guys, I need help with this one, Ive searched but cant find a way to test and replicate the conditions that Im seeing in my logs when someone trys to access one of my shares from outside through Apache2.
```

 --------------------- httpd Begin ------------------------ 

 
 Requests with error response codes
    405 Method Not Allowed
       /share: 3 Time(s)
 
 ---------------------- httpd End ------------------------- 



```

I often see lines like this in my morning Logwatch report.  I know theyre not successfully accessing the share but how are they doing this and how do I stop them?  Somehow theyre getting a list of all my shares and Ive gotta find out how.

---

### Post by simonplexus on 2011-04-30
check /var/log/apache2/access_log and error_log to see what they are pulling and to see if its the same IP all the time. It may just be as simple as scanners or crawlers - many look for simple things like '/share' '/admin' etc.

If its the same IP in the access or error logs thats trying to get in, you can run wireshark or tcpdump to find out a bit more about what they are doing

```

tcpdump -s9999 -X -w /tmp/capture.pcap host their.ip.address &

```

Then open up the file with wireshark to see what they are up to.

---

