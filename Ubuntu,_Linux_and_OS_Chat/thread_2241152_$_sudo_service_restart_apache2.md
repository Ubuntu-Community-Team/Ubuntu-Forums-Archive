---
title: "$ sudo service restart apache2"
date: 2014-08-24
forum: Ubuntu, Linux and OS Chat
---

### Post by IQAndreas on 2014-08-24
Since I don't speak like Yoda, I frequently flip around the arguments for [FONT=Courier New]service[/FONT] like this:

```
$ sudo service restart apache2
restart: unrecognized service
```

I made a tiny library which just gives you a nicer warning whenever this happens:

```
$ sudo service restart apache2
restart: unrecognized service
Did you mean 'service apache2 restart'?
```

All the source is on GitHub, and installed via a small bash [FONT=Courier New]install.sh[/FONT] script:

[[IMG]https://github.com/favicon.ico[/IMG] GitHub.com: IQAndreas/unrecognized-service-autocorrect](https://github.com/IQAndreas/unrecognized-service-autocorrect)

If anyone needs it, I don't personally make the following mistake, but I can easily modify the script for people who accidentally write
```
$ sudo restart service apache2
```

---

