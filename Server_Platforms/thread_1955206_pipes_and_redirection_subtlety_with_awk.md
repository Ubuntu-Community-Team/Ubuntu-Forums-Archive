---
title: "pipes and redirection subtlety with awk"
date: 2012-04-09
forum: Server Platforms
---

### Post by floobit on 2012-04-09
I'm not sure where to put this thread, as it's mostly just about pipes and redirection.  I am trying to write iostat statistics to a log file, so do something like this:

```
iostat sda 2 > today.log
```

But this gives me lots of unwanted text.  I could clean up the log file, but it would be quicker to use awk.  This line gives me exactly the numbers I want, printed onto the screen (user CPU and CPU spent waiting for IO):

```
iostat sda 2| awk 'NR%6==4{print $1 " " $4}' 
```

Unfortunately, this line creates a file with no contents:

```
iostat sda 2| awk 'NR%6==4{print $1 " " $4}' > today.log
```

Why?

---

