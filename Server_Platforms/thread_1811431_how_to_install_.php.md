---
title: "how to install .php"
date: 2011-07-24
forum: Server Platforms
---

### Post by Fertech on 2011-07-24
I'm using ubuntu 10.04 LTS how do I install .php from the terminal.

---

### Post by schnelle02 on 2011-07-25
sudo apt-get install php5

---

### Post by fdrake on 2011-07-25
Actually you need to install more than just that. I wrote a very dirty piece of script because i was tire to go everytime to the FAQ to install apache, php,mySQL,cgi,myPhpAdmin in every pc i was using . if you want you can dow2nload and try to see if it works. was written at 4am in 20min so don't judge me.

download and type
```

chomod +x apache_php.sh
sudo ./apache_php.sh
```

---

### Post by brighty22 on 2011-07-25
If you are using apache, try

```
sudo apt-get install libapache2-mod-php5
```

as you can then avoid editing apache config files directly. There are several extensions available that Google can help with finding - eg. if you want to use mysql with php you will need the php5-mysql package.

---

