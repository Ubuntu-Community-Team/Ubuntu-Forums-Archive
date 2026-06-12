---
title: "Apache error log not updating"
date: 2009-08-04
forum: Server Platforms
---

### Post by satish_j on 2009-08-04
Help needed relating to apache error log not updating on error in php script.
Location of the log is:/usr/local/apache2/htdocs/error.log
On starting apache,there are some entries in error log like:-
```

[Tue Aug 04 09:56:43 2009] [notice] Child 2040: Acquired the start mutex.
[Tue Aug 04 09:56:43 2009] [notice] Child 2040: Starting 250 worker threads.

```
But,on testing the php pages,if any error is encountered,the log is not reflecting the script error.

---

### Post by credobyte on 2009-08-04
Have you tried to change LogLevel ( [http://www.devshed.com/c/a/Apache/Logging-in-Apache/](http://www.devshed.com/c/a/Apache/Logging-in-Apache/) ) ?

---

### Post by satish_j on 2009-08-04
what level should be kept in order to capture php script errors??
Actually,i think this is a kind of nuisance.Log file is supposed to log all the events irrespective of criticality.
Is it possible to have all the loglevel settings instead of only one??

---

### Post by fahadsadah on 2009-08-04
Apache does not log PHP errors

---

### Post by satish_j on 2009-08-04
> **fahadsadah said:**
> Apache does not log PHP errors

Iam talking of PHP script errors at runtime on parsing by browser.I have this windows machine where the logs do update for every php parse error.It also uses apache server.

---

