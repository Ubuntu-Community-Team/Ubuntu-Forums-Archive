---
title: "Geoip connecting to internet at every boot"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nrundy on 2012-02-24
Since updating to 12.04 I've noticed Geoip is always connecting to the internet. Anyone know how to disable this service or at least stop it from connecting to the internet all the time?

I imagine this is a privacy concern. Can't this be used to track me? What exactly is it connecting for?

---

### Post by cariboo on 2012-02-24
Geoclue is tied to the date/time indicator to automagically set your time zone. The results it gets aren't very accurate, in my case it puts my location in the tee box of the 3rd hole of the local golf course, which is about 7 Km from where I live.

---

### Post by nrundy on 2012-02-25
I have no problem setting my time zone manually.

How do I disable this service so that it stops connecting to the internet at every boot?

---

### Post by cariboo on 2012-02-25
You can disable it by removing geoclue, but you will also lose the date/time indicator.

---

### Post by nrundy on 2012-02-25
So basically, with no application firewall available for linux, there is no way to block this.

And no setting to turn it off means users are stuck with it.

---

### Post by alphacrucis2 on 2012-02-25
In the settings dialogue you can turn off setting the time from the internet to set the time manually. Does that stop geoclue connecting out?

---

### Post by cariboo on 2012-02-25
> **nrundy said:**
> So basically, with no application firewall available for linux, there is no way to block this.

And no setting to turn it off means users are stuck with it.

I know you've been harping on this for a while, but it seems to me that if you want an application firewall, (I don't really like that term), that it might be an idea to start a development project yourself. Find a developer that is willing to work on something like that, and see what you can come up with.

---

### Post by chazinams on 2012-02-25
> **cariboo907 said:**
> Geoclue is tied to the date/time indicator to automagically set your time zone. The results it gets aren't very accurate, in my case it puts my location in the tee box of the 3rd hole of the local golf course, which is about 7 Km from where I live.

Does geoip take the place of NTP? Is it also setting the time so it's accurate? or is it just setting the time-zone?

---

### Post by cariboo on 2012-02-25
> **chazinams said:**
> Does geoip take the place of NTP? Is it also setting the time so it's accurate? or is it just setting the time-zone?

This is the description of the geoclue package from synaptic:

> GeoClue provides applications access to various geographical information
sources using a D-Bus API or a C library.

This package contains the master server for GeoClue.

Change the clock setting to manual, then killing /usr/lib/geoclue/geoclue-master and /usr/lib/ubuntu-geoip/ubuntu-geoip-provider, seems to close the connection, I'll have to wait for a reboot to see if the settings stick.

---

### Post by chazinams on 2012-02-25
I actually already read that in synaptic, but I don't understand any of it :)

Do you know any examples of what services it provides applications? Is it like a cell phone that can be tracked physically where ever it goes?

---

### Post by cariboo on 2012-02-26
Geoip isn't as accurate as what is used to track cell phones. My smartphone can find my location within a couple of meters, whereas geoip puts my location within several km/miles of where I actually am.

I personally don't care if my location is tracked, but there should be a way to turn it off for those that don't want this feature.

---

