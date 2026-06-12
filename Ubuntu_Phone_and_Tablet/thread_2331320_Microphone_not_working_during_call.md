---
title: "Microphone not working during call"
date: 2016-07-20
forum: Ubuntu Phone and Tablet
---

### Post by jpgemble-0 on 2016-07-20
Hi all,

I've bought a BQ Aquaris E4.5 Ubuntu Edition a few weeks ago.
I was very happy to buy it but I have a big issue during phone calls: sometimes (very often in fact) no sound is sent from my microphone to the person I'm speaking to. For a phone, it's very annoying :cry:
It has started the first day and during all these weeks I have not been able to find how that happens or stops.
Here is all what I know:

[LIST]
[*]My version is OTA-11.
[*]When it happens it's for a long time. It wasn't working at all during the last 3 days.
[*]It has never work properly for more than 1 day.
[*]I've first thought that plugging/unplugging an headphone jack solves the problem (only after the call) but last week it hasn't.
[*]Clicking on the speaker icon always allows my interlocutor to ear me. When I click again to come back in the previous state, it still not working.
[*]The interlocutor can ear a very small noise. Clicking on the microphone icon to mute stops the noise. When I click again to come back in the previous state, it still not working and the noise can be eared again.
[*]If I plug an hand free headset it works properly (but the embedded microphone is then not used). It's the workaround I actually use.
[*]Some applications that uses the microphone works properly. I've tried "Recorder" and "Guitar tools".
[*]It seems that, when it happens, the battery empty quickly (100% to 0% in about 20h against more than 3 days). No GPS, no bluetooth, no Wi-Fi, no 3G, no more than 10 minutes of call, no games. In short, nothing.
[*]Having the screen locked or not when receiving a call doesn't change anything.
[*]Incoming call or outgoing call doesn't change anything.
[*]My phone is configured in silent mode.
[*]I use the alarm clock every morning.
[*]I put my phone in the plane mode every night.
[/LIST]
So, as my microphone works with some applications and during calls when I click on the speaker, I believe that it's not an hardware issue but a software one.
I thought to a bad microphone volume in pulseaudio settings but I've not been able to find the information within the profile management.

Any help to diagnose this issue (and solve it) would be greatly appreciated.
If it's a software issue, I don't understand why I would be the only one to have it.

Thanks,

Jean-Pierre

---

### Post by bleizh on 2016-07-27
I've exactly the same issue with a BQ Aquaris E4.5 Ubuntu Edition ! Did you find a work around ?
amicalement ;)

Bleizh

Edit : I've exactly the same issue but allways. The phone is new. microphone is working well with all other apps. I belive this is a software issue too but didn't manage to solve it.

---

### Post by jpgemble-0 on 2016-07-31
Hi Bleizh,

No it still doesn't work.

I've upgraded to OTA-12 and it has worked for about 1 day before having exactly the same issue.
I've made the update the evening and the following morning, at about 9:00, I've called my phone with another phone to make a test and it was working.
I had my phone in my pocket all the day and I haven't used it at all.
I've received a call at about 18:00 and it was no longer working.
I don't see what makes it going wrong. The only actions that might have happened are buttons ones (in my pocket) and network ones (old GSM only). I haven't receive any SMS during this day.

I was hoping that the community could help me but, as the only reply is another guy that have the same issue, I will have to manage it by myself.
I'm a software and firmware developer so my plan is to look into the code and make a custom debug version.
But for now I have a hard time to understand where does the code OTA-12 for my BQ Aquaris E4.5 come from.
The Aquaris E4.5 branch ( [https://github.com/bq/aquaris-E4.5](https://github.com/bq/aquaris-E4.5) ) is 1 year old.

Best regards,

Jean-Pierre

---

### Post by PaulW2U on 2016-07-31
> **jpgemble-0 said:**
> I was hoping that the community could help me but, as the only reply is another guy that have the same issue, I will have to manage it by myself.
Jean-Pierre, are you aware of the Ubuntu Phone mailing list which is hosted on Launchpad?

The list has over 1500 subscribers including several developers and Canonical employees - [https://launchpad.net/~ubuntu-phone](https://launchpad.net/~ubuntu-phone)

---

### Post by jpgemble-0 on 2016-07-31
Thank you PaulW2U.

I was aware of the maing list.
When I've posted my issue I've guested that this forum was a better place.
For starting development stuff, I'm searching available web resources before annoying mailing list guys.

Best Regards,

Jean-Pierre

---

### Post by bleizh on 2016-08-22
Hélas ! I give up !
I've re-flashed the phone but still had the exact same issue. OTA 11 or 12 didn't solve anything. I tried and tried and tried... Nothing.

As the microphone has never worked during calls and because the phone was brand new, i returned it for replacement. But it seems there are no more stock...

A suivre...

---

### Post by wlbi on 2016-09-24
Is it better with OTA 13? I also use the [COLOR=#000000]BQ Aquaris E4.5 Ubuntu Edition[/COLOR] as a daily driver since may 2015, but never experience that problem. Maybe it's a hardware bug? :confused:

---

