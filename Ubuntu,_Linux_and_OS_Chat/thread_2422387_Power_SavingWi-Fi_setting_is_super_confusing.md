---
title: "Power Saving/Wi-Fi setting is super confusing"
date: 2019-07-06
forum: Ubuntu, Linux and OS Chat
---

### Post by motrek on 2019-07-06
I don't know if this is the right place, but I have a complaint about the Power Saving settings panel.

So under Power Saving, there's a Wi-Fi setting that can be toggled on/off.

The description line is "Turn off Wi-Fi to save power."

So what does this setting do? Since it's under Power Saving, it's presumably a power-saving Wi-Fi setting... based on the description line, it probably turns off Wi-Fi automatically when not in use... right?

Wrong.

Turns out, it has ***nothing at all*** to do with power saving. It's just whether or not Wi-Fi is turned on. When the toggle button says on, Wi-Fi is on. When the toggle button says off, Wi-Fi is off. What the hell?!

I got tricked by this and accidentally turned off Wi-Fi on my headless workstation. I had to spend 10 minutes dragging the thing downstairs, connecting it to a monitor/keyboard/mouse, turning Wi-Fi back on, disconnecting everything, and dragging it back upstairs.

I took a screen shot of this setting and sent it to a few friends of mine... not a single one of them believed me, that the setting *(under Power Saving)* just turned Wi-Fi on and off.

---

### Post by Geoffrey_Arndt on 2019-07-07
The description seems clear to me.

   If you toggle the WiFi off, it is off and you will save on power when running the Laptop or Notebook PC in "offline mode" (like updating a spreadsheet or running dozens of other native apps _that do not need internet_).  Right below that setting is the toggle to turn off Bluetooth - for the same exact reason.  In fact each option has a caption below it "wifi can be turned off to save power" . . . ditto for bluetooth.

So, it seems that you _read more into the explanatory text_ than required (stop thinking so hard!) ):P

---

### Post by motrek on 2019-07-07
Disagree 100%.

It's *super* confusing to have a general, basic network hardware setting under the "Power Saving" menu.

The Power Saving menu should be for Power Saving features, no?

You can also save power by turning off your computer entirely, but the Power Saving menu doesn't have a confusing option to do that. Something for the next version?

---

### Post by coffeecat on 2019-07-07
> **motrek said:**
> I don't know if this is the right place,

It isn't.

> **motrek said:**
> I have a complaint

Who do you believe you are complaining to? The forum membership, staff included, are volunteer end-users like yourself. Ubuntu forums is for technical peer support for Ubuntu. Discussion areas such as this are for - well - discussions. From the Ubuntu' Linux & OS Chat sub-forum strapline:

> This is the place for chat and discussion about any aspect of Ubuntu, Linux or any operating system and its software. Technical support requests should be posted in an appropriate support sub-forum. Discussion of the politics of open source is permissible, but only the politics of open source. Wider political discussion is disallowed in all areas of the forum, as is discussion of religion. As with the Cafe, **this area is intended for fun and community building, not arguments.** Please take those elsewhere. Thanks! 

(My bold.)

> **motrek said:**
> The Power Saving menu should be for Power Saving features, no?

Yep.

For what it's worth, and this is just my opinion, "Turn off Wi-Fi to save power," seems pretty unambiguous and clear to me. When using my mobile phone, if I want to preserve battery life and save power, I switch off wireless and bluetooth. Ditto when using a laptop and have no need to connect to something. There's nothing in "Turn off Wi-Fi to save power," that implies some sort of low level minimal power use wifi. It says "turn off", not "turn down". A power saving setting in the power saving menu.

However, in response to Geoffrey_Arndt, you said,

> **motrek said:**
> Disagree 100%.

It doesn't sound as though you are prepared to be open to others' opinions and points of view. When using our chat areas, you might find that a readiness to listen to others could be beneficial.

---

### Post by motrek on 2019-07-07
> **coffeecat said:**
> It isn't.

Okay, cool, thank you. I actually googled for probably 5-10 minutes on what I could do to leave feedback on this UI and this is the best I found. If you google "leave feedback on Ubuntu UI" and click around, you can find 100 ways to get support for Ubuntu but I couldn't find any way to leave feedback. This is actually the only site/forum I could find that isn't explicitly/exclusively for support. If you can point me in the right direction here, I would really appreciate it.

> For what it's worth, and this is just my opinion, "Turn off Wi-Fi to save power," seems pretty unambiguous and clear to me.

Sure, everything is great if you understand that that label is a tip/instruction, and not the name or explanation for a setting.

If you have a setting, and it's labeled "Turn off a thing," and it's set to "ON", then doesn't that imply to you that the thing will be turned *off*? I mean, it's not quite a double-negative situation but it reminds me of one.

---

### Post by uRock on 2019-07-07
I haven't had any misconceptions of these power saving functions, either. I have never used it on my computers, but I do shut off WiFi and Bluetooth on my phone to save battery life.

---

### Post by motrek on 2019-07-07
Got it, thanks for the tip re: GNOME.

To be clear, I don't have any misconceptions about whether or not turning off wi-fi saves power either.

But the ability to turn something off isn't a *power saving feature* and I think it clearly shouldn't be in the power saving settings panel.

As a bit of context, I was using my headless workstation with a fresh install of Ubuntu and after a few minutes the screen started to dim. This is obviously a feature I don't want on a headless machine so I went to the Power Saving panel to turn it off.

Then I saw a setting labeled "Turn off Wi-Fi..." and it was turned ON, and I thought, "oh s**t, why would I ever want Wi-Fi turned off on this machine, I better set that to off..." and here we are.

---

