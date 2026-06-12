---
title: "Apache Error: &quot;undefined&quot; being requested."
date: 2010-12-17
forum: Server Platforms
---

### Post by gjj391 on 2010-12-17
I am getting a very odd error in my Apache error_log. It seems to be related to downloading assets such as JavaScript files.

An example error entry looks like:

[error] File does not exist: /webroot/site/undefined

I am not requesting any asset with that file path and its not consistent, but it is happening a good bit. 

Any ideas out there?

---

### Post by James78 on 2010-12-17
I found this after searching around:
"This is pretty certainly an error in your Javascript. Look out for any places where JS requests a file named "webroot/site"+some_variable - the some_variable part is undefined for some reason"

Maybe it hopefully is applicable to your case? Since you know what might be the cause now you can do some testing on this..

---

