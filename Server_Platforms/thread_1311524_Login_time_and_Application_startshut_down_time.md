---
title: "Login time and Application start/shut down time"
date: 2009-11-02
forum: Server Platforms
---

### Post by ndnd on 2009-11-02
Hi,
I am new to UBUNTU and wanted to know if I can do the following 

I am using the Ubunt server edition 8.10 

1) Easily get the login/logout time - so total usage (in terms of hours) for a user) 

2) Get the usage hours of a specific application installed on Ubuntu- for e.g if a user starts an application - works on it for about 1 hour and shuts it down - Can I get the time user started using the application and the time it was shut down. 

I need to determine the usage of accounts and specific applications the user is using

thanks in advance

---

### Post by ndnd on 2009-11-05
Hi,
I am trying to search for a login file. I can't seem to find anything from the forum posts - am I posting this in the wrong section? :D

---

### Post by sprouty on 2009-11-05
from the terminal try

```
last
```

or

```
lastlog
```

might help you.

---

