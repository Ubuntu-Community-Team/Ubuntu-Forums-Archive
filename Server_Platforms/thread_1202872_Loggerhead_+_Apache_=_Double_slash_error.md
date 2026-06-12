---
title: "Loggerhead + Apache = Double slash error"
date: 2009-07-02
forum: Server Platforms
---

### Post by kylehotchkiss on 2009-07-02
I have loggerhead set up on an apache proxy and it works fine other then this annoying bug: it has to have a double slash in the url to work right.

for example:

[http://server/code/websites/example.com](http://server/code/websites/example.com)

would load an error message in the wsgi server (the one running loggerhead)

but [http://server/code//websites/example.com](http://server/code//websites/example.com)

works fine,
I don't understand the problem and it's really annoying.

thanks for any help =)

---

