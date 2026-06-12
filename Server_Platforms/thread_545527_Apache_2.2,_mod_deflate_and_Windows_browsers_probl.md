---
title: "Apache 2.2, mod_deflate and Windows browsers problem"
date: 2007-09-07
forum: Server Platforms
---

### Post by unixhead on 2007-09-07
Here's my problem:
I have a lot of JSON coming from the server in my application. So after turning on deflate (I'm using Apache 2.2.3 if it does matter) I get size of trasferred data reduced from 200 to 8 kb. In Windows versions of Firefox I see all required content type and accept headers being sent (using Firebug). But still an uncompressed content comes back.

In Linux version of Firefox everything is fine as I mentioned above. What's the reason and how people deal with IE that doesn't recognize deflated content?

Here's my conf:
```

  # Deflate
  AddOutputFilterByType DEFLATE text/html
  AddOutputFilterByType DEFLATE text/plain
  AddOutputFilterByType DEFLATE text/xml
  AddOutputFilterByType DEFLATE application/x-javascript
  AddOutputFilterByType DEFLATE text/css
  AddOutputFilterByType DEFLATE application/json

  BrowserMatch ^Mozilla/4 gzip-only-text/html
  BrowserMatch ^Mozilla/4\.0[678] no-gzip
  BrowserMatch \bMSI[E] !no-gzip !gzip-only-text/html

  Header append Vary User-Agent env=!dont-vary

  DeflateFilterNote Input input_info
  DeflateFilterNote Output output_info
  DeflateFilterNote Ratio ratio_info
  LogFormat '"%r" %{output_info}n/%{input_info}n (%{ratio_info}n%%) -- "%{User-agent}i"' deflate

#  DeflateFilterNote ratio
#  LogFormat '"%r" %b (%{ratio}n) "%{User-agent}i"' deflate

```

Thanks.

---

### Post by pancham.singh@gmail.com on 2008-02-17
Were you able to resolve this? I am having the same problem on Windows Vista? However, it works fine on Windows XP.

---

