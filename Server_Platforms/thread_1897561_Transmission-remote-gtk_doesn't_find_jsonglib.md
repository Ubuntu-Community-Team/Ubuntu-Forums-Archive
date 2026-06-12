---
title: "Transmission-remote-gtk doesn't find jsonglib"
date: 2011-12-19
forum: Server Platforms
---

### Post by czesu on 2011-12-19
Hello, in Ubuntu json-glib-1.0 package is named gir1.2-json-glib-1.0. Because of that Transmission-remote-gtk doesn't want to install itself:
```

$ ./configure
(...)
checking for jsonglib... no
configure: error: Package requirements (json-glib-1.0 >= 0.8) were not met:

No package 'json-glib-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables jsonglib_CFLAGS
and jsonglib_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
Could somebody tell me where can I adjust that PKG_CONFIG_PATH and what should it look like?

---

