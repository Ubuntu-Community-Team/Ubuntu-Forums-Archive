---
title: "Upstart XVFB Selenium"
date: 2014-01-05
forum: Server Platforms
---

### Post by mastermindg on 2014-01-05
I've setup Selenium (an automation testing platform) on my headless server. Selenium requires an X display to open up browsers for testing. I have an existing init service setup for Selenium where it is launched via **XVFB-RUN**:

```
xvfb-run java -jar selenium.jar > /tmp/selenium.pid > /dev/null 2>&1
```

I have a couple issues with this configuration:

[LIST=1]
[*]Pid Management - the pid isn't picked up for Selenium as it's wrapped in XVFB-RUN.
[*]Starting as another user - i want to run this as www-data so that files can be manipulated in my test environment
[*]
[/LIST]

Another possible way to start Selenium might be by assigning it to an existing X-Display (starting XVFB separately) but I'm not sure if this is possible.

How can I setup an Upstart job that can manage Selenium under an X-Display? I wa

---

