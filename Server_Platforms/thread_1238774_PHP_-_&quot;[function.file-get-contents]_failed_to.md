---
title: "PHP - &quot;[function.file-get-contents]: failed to open stream: HTTP request failed!&quot;"
date: 2009-08-12
forum: Server Platforms
---

### Post by dbone on 2009-08-12
Running a default install of Server 9 and getting the following error when trying to use file_get_contents(). 

```
**Warning**:  file_get_contents(http://www.yahoo.com) [[function.file-get-contents]("http://senior.com/function.file-get-contents")]: failed to open stream: HTTP request failed!
```This same issue occurs for any URL.

1. I checked php.ini for allow_url_fopen and it's set to On. 
2. Also set the user_agent to Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0).
3. Have complete internet access on server, DNS works.
4. curl works properly.
5. Existing scripts are using the file_get_contents and it would take a lot of effort to convert.

I noticed that the default PHP installation has the Suhosin patch. Could this be causing the issue?

I've been pulling my hair out on this one. If you can help me solve I will "donate" $20 to you. No joke.

---

### Post by dbone on 2009-08-13
Ended up being a firewall issue. Content filtering was dropping packets...

---

### Post by mikejarema on 2011-07-06
dbone, I'm seeing this issue on one of my client's dev servers.  How did you manage to isolate it to the firewall?

---

