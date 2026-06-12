---
title: "Querying source of packages?"
date: 2007-11-10
forum: Server Platforms
---

### Post by LennartH on 2007-11-10
Hi!

I've got a virtual server which I want to use as a public webserver.
Ubuntu version is Dapper.

```
dpkg -l | egrep '^ii'
```
With dpkg I can list the installed packages. There are about 160 packages.

Is it possible to get a list which shows the source (repository and component) of every package?

Best regards
Lennart

---

### Post by LennartH on 2007-11-10
Sorry - it's not really a server question. Came to my mind too late.

Bye
Lennart

---

### Post by koenn on 2007-11-10
> **LennartH said:**
> Hi!

I've got a virtual server which I want to use as a public webserver.
Ubuntu version is Dapper.

```
dpkg -l | egrep '^ii'
```
With dpkg I can list the installed packages. There are about 160 packages.

Is it possible to get a list which shows the source (repository and component) of every package?

Best regards
Lennart
The repo / component is not a property of the package itself, but of the system it's installed on so I don't know if there's an easy way to do this, but you can do
```
apt-cache policy  package_name
```
and it will show you where your computer has installed package_name from or would install package_name from.

You could probably cook something up like 
```
for item in list_of_pakages; do
     apt-cache policy $item  | grep something_relevant
```

---

### Post by LennartH on 2007-11-11
Hi koenn!

With your help I wrote the following script:

```
#!/bin/bash

dpkg -l | egrep '^ii' | cut -d' ' -f3 > tmpPackages.txt

while read item; do
    echo $item
    apt-cache policy $item  | egrep ' 500 '
done < tmpPackages.txt
```

Output looks like this:
```
adduser
        500 http://archive.ubuntu.com dapper/main Packages
[...]
```

Thanks a lot!
Lennart

---

