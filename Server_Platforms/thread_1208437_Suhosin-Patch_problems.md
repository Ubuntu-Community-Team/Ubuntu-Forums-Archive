---
title: "Suhosin-Patch problems"
date: 2009-07-09
forum: Server Platforms
---

### Post by Stephen_at on 2009-07-09
OK, I'm getting pretty annoyed with this. I'm running 8.0.4 LTS with php5 which is compiled with the so called Suhosin-Patch in it (as provided by Ubuntu), on a AMD64 X2 processor.

Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.6 with Suhosin-Patch mod_ssl/2.2.8 OpenSSL/0.9.8g 

Now it keeps crashing out with the following message:

ALERT - canary mismatch on efree() - heap overflow detected.

There is no rhyme or reason as to which php file causes this. I'm seeing it at various times with various php files in WPMU and PHPBB3 and of course everyone just turns round and says its the Suhosin-Patch that is defective. Sometimes I can keep the server running for days with no problems them sometimes I need to restart it twice in the same day.

The version of the Suhosin-Patch provided by Ubuntu is 0.9.6.2 which dates from November 2006. The current version is 0.9.7 (March 2009).

Is there any plan to either:

a) Provide a version of php without the patch in it?
b) Provide a version of php with a newer version of the patch in it?

If the answer to the above question is neither can someone please point me to a good tutorial on how to recompile the php configuration shipped by ubuntu but without the patch. I've found 
[http://chrisblunt.com/blog/2009/05/01/php-fixing-mismatched-canaries-how-to-remove-suhosin-from-debianubuntu-packages/](http://chrisblunt.com/blog/2009/05/01/php-fixing-mismatched-canaries-how-to-remove-suhosin-from-debianubuntu-packages/)

but wasn't sure if this was the best one to follow.

---

### Post by liquidApe on 2009-07-27
I just started having the same problem last week after upgrading through the synaptic manager.

I have noticed that mssql queries with results longer then 5 characters are breaking.


"Select joe, 1000"  works
"Select joe, 10000" breaks
"Select 1, 2, 3, 4, 5" works
"Select, 1, 2000, 3, 4, 5" works
"Select, 1, 20000, 3, 4, 5" breaks


I'm also on 8.04 LTS/PHP5 and getting "canary mismatch on efree() - heap overflow detected.

---

