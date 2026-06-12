---
title: "Possible serious security hole."
date: 2012-03-11
forum: Ubuntu One (CLOSED)
---

### Post by RichardUK on 2012-03-11
Changed my password, old password still works!

I have Ubuntu One on my home and work PC's (both Ubuntu) and on my phone. Really impressed with the service. I was setting up a new PC and was setting up Ubuntu One, again this is a Ubuntu PC. 

I found that I had not written down my password in my normal place, a little book secured in my home office. So I reset the password and this time wrote it down. I expected my existing PC's and phone to then logout or complain about no access because they would still be using the old password. But to my surprise they are still connecting to Ubuntu One, reading and writing files. 

Is this a feature? If it's a bug should I log it? I tried to Google for it and found no hits.

---

### Post by imachavel on 2012-03-11
definitely log it now. ubuntu one server seems to have serious bugs in the server warehouse. Where? Only the administrators would be able to tell you that.
 
being able to use your old password? I thought you were going to complain about the browser you are using and I'd say try a browser with embedded encryption or what not. Weird man that is a definite error being able to use two passwords. Thank god I'm not the only one experiencing errors, there seems to be some serious bugs in the system most likely software level as hardware/modem/router level would just be a complete failure. Only unable to connect issues are unknown if it's at the user level, server hardware or server software level. Then trouble shooting begins.

There is no way, a password that is stored on their server, could be user level. I hope they get this worked out, it should be easier then fixing windows with a virus, as fixing windows with a virus you might get a new virus the next day even if you create a brand new build, with a brand new hdd, and format a new partition with brand new windows OS and activation, you can with good virus protection still get a brand new virus the next day if the user does not know what they are doing. Lol I'd imagine fixing the web servers, the ubuntu one team might not have to trouble shoot the same errors for weeks/months/possibly years. Well, I hope you and I both get a good reply very soon.

---

### Post by RichardUK on 2012-03-11
I added a bug as I thought that as with any other password access controlled service it would have prevented any device using the old credentials to have been looked out. Seems I was wrong and the behaviour I have seen is correct, here is the reply to my listed bug. I have to say, very impressed with the fast response to my bug posting. :)

> 
This is expected behaviour.

Ubuntu One does not store your password anywhere, it uses them to obtain
credentials for each specific device. So, if you want to make it so a
device is locked out, you can do it by removing its credentials, or from
out website, where you can see a list of your authenticated devices.


---

