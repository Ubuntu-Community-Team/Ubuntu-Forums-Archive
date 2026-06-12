---
title: "How to bind restart without loosing cache"
date: 2013-08-01
forum: Server Platforms
---

### Post by learnbash on 2013-08-01
[COLOR=#000000][FONT=verdana]Hi Folks,[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]I have a question that, if i want to add or modify zone files in dns, then how to reload the setting without clearing the cache. Is there any possibility. Please tell me.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Regards,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]BAS[/FONT][/COLOR]

---

### Post by papibe on 2013-08-01
Hi learnbash.

You should be able to do by reloading the zone:
```
sudo rndc reload yourdomain.com
```
Where 'yourdomain.com' is the zone you just modified. Don't forget to increase the SOA's serial number or bind will ignore the changes.

Let us know how it goes.
Regards.

---

### Post by SeijiSensei on 2013-08-02
You can force named to reload its configuration with either

```
kill -HUP pid_of_named
```

where pid_of_named is the appropriate process ID,

or, more easily,

```
killall -HUP named
```

---

