---
title: "How can I test if my computer is enforcing UEFI?"
date: 2022-05-04
forum: Security
---

### Post by Paddy Landau on 2022-05-04
I'm trying to find out how to test if my computer enforces UEFI (Secure Boot).

Every answer that I find on the internet tells me how to find out if it's *supported*, but not if it's *enforced*.

Is there a way for me to try to start (say) a Live USB in non-UEFI mode to see if it fails? How can I test conclusively that my computer enforces, or doesn't enforce, UEFI?

---

### Post by #&amp;thj^% on 2022-05-04
> **Paddy Landau said:**
>  How can I test conclusively that my computer enforces, or doesn't enforce, UEFI?

This tells me mine does:
```
if test -d /sys/firmware/efi;then echo efi;else echo bios;fi
efi

```
on kvm:
```
if test -d /sys/firmware/efi;then echo efi;else echo bios;fi
bios

```
you also asked about Secure Boot
```
mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode

```
I don't want Secure Boot enabled.

---

### Post by Paddy Landau on 2022-05-04
Thank you, @1fallen. My mokutil shows, "SecureBoot enabled". If I understand correctly, this means that Secure Boot is enforced. Is that correct?

---

### Post by #&amp;thj^% on 2022-05-04
> **Paddy Landau said:**
>  If I understand correctly, this means that Secure Boot is enforced. Is that correct?

Yes Sir.

---

### Post by Paddy Landau on 2022-05-04
> **1fallen said:**
> Yes Sir.
Thank you!

---

### Post by #&amp;thj^% on 2022-05-04
Your very welcome. But you did the work. :)

---

### Post by tea for one on 2022-05-04
> **Paddy Landau said:**
> I'm trying to find out how to test if my computer enforces UEFI (Secure Boot).
Every answer that I find on the internet tells me how to find out if it's *supported*, but not if it's *enforced*.
Is there a way for me to try to start (say) a Live USB in non-UEFI mode to see if it fails? How can I test conclusively that my computer enforces, or doesn't enforce, UEFI?

In your UEFI/BIOS Set Up, you may have the option to turn on Legacy support.
If you can enable Legacy support together with UEFI, then you have two choices when booting a Live USB.

I've attached two images.
One shows where I can enable both Legacy and UEFI and /or enable one or the other. (Your firmware will probably have a different set of menus/options).
The other displays the two version of booting a Live USB.

Any help?[ATTACH=CONFIG]290397[/ATTACH][ATTACH=CONFIG]290399[/ATTACH]

---

### Post by Paddy Landau on 2022-05-04
> **tea for one said:**
> If you can enable Legacy support together with UEFI, then you have two choices when booting a Live USB.
Thank you. This is what I want to prevent. It shouldn't permit legacy boot.

---

### Post by #&amp;thj^% on 2022-05-04
Most of the newer machines will only have UEFI and no Legacy Bios.

---

### Post by tea for one on 2022-05-04
> **Paddy Landau said:**
> Thank you. This is what I want to prevent. It shouldn't permit legacy boot.

Agreed, I only enable UEFI in the firmware - Legacy is permanently disabled.
Following on from 1fallen's comment that new PCs will only support UEFI, I have also read that some distributions are considering removing Legacy boot mode.
[https://fedoraproject.org/wiki/Changes/DeprecateLegacyBIOS](https://fedoraproject.org/wiki/Changes/DeprecateLegacyBIOS)

---

### Post by #&amp;thj^% on 2022-05-04
> **tea for one said:**
> I have also read that some distributions are considering removing Legacy boot mode.
[https://fedoraproject.org/wiki/Changes/DeprecateLegacyBIOS](https://fedoraproject.org/wiki/Changes/DeprecateLegacyBIOS)
That will be a very sad day, for many who rely on older hardware.
Thanks for the link.

---

### Post by DuckHook on 2022-05-04
> **1fallen said:**
> That will be a very sad day, for many who rely on older hardware&#8230;
Fedora has made no secret of their disinterest&#8212;some would say "disdain"&#8212;for legacy HW. OTOH, Slack has made no secret of their disinterest for bleeding edge HW. All's fair in love and war I guess.

The days of 32-bit and legacy HW are numbered in Ubuntu too. I intend to go to Debian for such HW when the time comes.

---

### Post by Paddy Landau on 2022-05-05
Given the rapidly-dropping prices for the same level of hardware, the time is approaching when 32-bit will be completely redundant. No one still supports 16-bit, for example; it won't be much longer before no one supports 32-bit.

Not yet, because there are people in poor areas of the world for whom upgrading their hardware is unrealistic (these days, even in the rich world), but it's coming. In the meantime, they'll have to rely on speciality distributions. Even Lubuntu, the only official distribution that caters for older hardware, supports 64-bit only.

I'm sure that the same will apply to Legacy mode.

[Bodhi]("https://www.bodhilinux.com/") is the only example of extremely light 32-bit (unofficial) Ubuntu derivative that I know of. I'm sure that there are others.

---

