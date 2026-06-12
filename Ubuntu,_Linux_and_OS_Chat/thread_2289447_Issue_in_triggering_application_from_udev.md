---
title: "Issue in triggering application from udev"
date: 2015-08-04
forum: Ubuntu, Linux and OS Chat
---

### Post by lyf on 2015-08-04
Hi Experts,

I am writing a udev rules file to trigger an application on the device arrival.

When the device is arrived the application A is triggered and it is running in infinite loop.

When the device is removed the application B is expected to run but it is not invoked instead application A is still running.

When I force killed the application A using pkill command then the application B is invoked. i.e Application B is queued until the application A is exiting.


In this case how to trigger a background application which will be triggered irrespective of each other dependency.

---

