---
title: "ProFTPd and non-ASCII passwords"
date: 2010-08-04
forum: Server Platforms
---

### Post by forbjok on 2010-08-04
Users who have passwords that contain non-ASCII characters (in this case a euro sign €, but probably others as well) are unable to login via FTP to the ProFTPd server. The FileZilla client states that the server "might not be UTF-8 aware", and then fails to authenticate.

I've tried "UseEncoding on" (it wouldn't accept putting anything except 'on'/'off' as the argument), and that didn't fix it.
I also tried "LangDefault <some UTF-8 locale>", but I couldn't find any locale it would accept. When using the "en_US.UTF-8" or "en_US.utf8" locales, which is the standard locale used by the server, it simply said it was "not a supported language".

Is there any way to make ProFTPd support passwords containing non-ASCII characters?

---

