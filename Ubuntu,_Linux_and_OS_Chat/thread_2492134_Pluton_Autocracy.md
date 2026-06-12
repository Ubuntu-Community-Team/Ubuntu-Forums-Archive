---
title: "Pluton Autocracy"
date: 2023-10-31
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2023-10-31
I've posted about Microsoft's "Pluton" Technology before...  But I am wondering what options will Linux users have in the future, if they don't want to be a part of this nonsense.

If you haven't heard of Pluton, check here:  [https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/]("https://www.microsoft.com/security/blog/2020/11/17/meet-the-microsoft-pluton-processor-the-security-chip-designed-for-the-future-of-windows-pcs/")
or here: [https://www.starwindsoftware.com/blog/what-is-microsoft-pluton-security-processor]("https://www.starwindsoftware.com/blog/what-is-microsoft-pluton-security-processor")

It is shaping up to be complete and total control of your home computing device by one company.
What are we going to be able to purchase?  I mean, realistically, if Pluton is a part of Intel and AMD, our alternatives are very limited.

---

### Post by ian-weisser on 2023-11-01
There are currently major vendors that ship Ubuntu Desktop in addition to MS Windows. You get to choose which you want.

Were major vendors to eliminate such choice, one imagines the also-already-existing niche Linux-only Desktop/Laptop vendors would likely thrive with less competition.

---

### Post by tea for one on 2023-11-01
More (possibly useful) info here [https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3](https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3)

3rd party UEFI CA [https://www.phoronix.com/review/rembrandt-linux-boot](https://www.phoronix.com/review/rembrandt-linux-boot)

---

### Post by Shibblet on 2023-11-01
> **tea for one said:**
> More (possibly useful) info here [https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3](https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3)
Amazing... some of the comments on the thread on this link, met with the same concept I titled this thread.  Plutocracy.

3rd party UEFI CA [https://www.phoronix.com/review/rembrandt-linux-boot](https://www.phoronix.com/review/rembrandt-linux-boot)
Secure Boot has always been a thorn in Linux' paw.

Where I am glad that Torvalds merged the code into the Linux Kernel, and that Ubuntu (Canonical) has decide to support Secure Boot, it still isn't a fair market.
This is literally a professional decision based on the old adage "If you can't beat them, join them."

I look at it like this.  Microsoft comes up with a new technology, and calls it something trendy like "Basic Use."  They work it into their OS, and then tell manufacturers they have to support "Basic Use" in their hardware.  Then, any software that doesn't support "Basic Use" is incompatible.

So, when Canonical sees that without "Basic Use" compatibility, their OS would be useless, they decided to add compatibility into their own software...  They still are playing Microsoft's Game.  Microsoft owns the computer market, and is compelling hardware and software manufacturers to add in their own form of complete control.

Soon, we will not be able to buy a computer that isn't controlled by Microsoft.  

ARM isn't a viable solution. Now that this has started:  [https://www.reuters.com/technology/nvidia-make-arm-based-pc-chips-major-new-challenge-intel-2023-10-23/]("https://www.reuters.com/technology/nvidia-make-arm-based-pc-chips-major-new-challenge-intel-2023-10-23/")
And no one else except AMD and Intel have x86 and x64 licenses.

---

### Post by ian-weisser on 2023-11-01
> **Shibblet said:**
> 
Soon, we will not be able to buy a computer that isn't controlled by Microsoft.  


Huh? That dystopian future occurred 15 years ago.

Lost its scare value over the years. Still annoying, though.

---

### Post by tea for one on 2023-11-02
> **Shibblet said:**
> Soon, we will not be able to buy a computer that isn't controlled by Microsoft.
No more Barebones PCs?
I'll look after mine with great care because, if your theory is correct, I'm sitting on an appreciating asset.

> Bare metal Linux just means that Linux is running directly on the device hardware
Taken from this  page dated 25 October 2023
[https://learn.microsoft.com/en-us/linux/install](https://learn.microsoft.com/en-us/linux/install)

---

### Post by grahammechanical on 2023-11-02
Is Pluton an improvement to hardware security? Or, a Microsoft cunning plan? I am not qualified to judge. I do have opinions.

Makers of motherboards are fitting Pluton chips as standard. They have to do this if they want their motherboards to compete against the offering of their rivals. A year ago I purchased an OEM laptop made in Taiwan. This laptop has a Pluton chip. The UEFI utility gives access to the settings of TPM and Software Guard eXtentions (SGX).

I purchased the laptop from an English supplier who sold it with Ubuntu 20.04 pre-installed. When I boot the machine I see an error message: "firmware bug. TPM interrupt not working. Polling inst."

This happens after Grub has done its job. It tells me that Linux is aware of the TPM but can do nothing with it. I get this same error message with Ubuntu 22.04 and Ubuntu 23.10 (development branch). But I do not see that error message now that 23.10 has become the release version. This tells me that Ubuntu knows about the TPM and possibly can do something with it.

In my mind it makes sense for Linux and Ubuntu developers know how to work with the Pluton chip. It may even be useful on certain hardware such as server systems. This is outside my experience.

Do we want Ubuntu to be able to dual boot with Windows? That will not happen if the workings of the Pluton chip are ignored. Do we want the "Erase disk and install Ubuntu" option to turn the machine into an expensive brick? That may happen if Windows is erased after it has taken ownership of the TPM. Microsoft uses the expression: "Takes ownership." I see nothing wrong with Ubuntu having the capacity to "take ownership" of the TPM. 

It may even be a useful ability. I suspect that for home users it may complicate matters. Another layer or two of passwords that a user can forget. There are passwords for the motherboard; the UEFI utility: the TPM and then there is full disc encryption. 

Anyway, these are my opinions

P.S. bare bones machines may require special hardware drivers to give full functionality to the keyboard. My laptop does. The supplier provided those drivers when it installed 20.04. It also has a repository. I am able to put that repository as a software source in 22.04 and 23.10 and install the keyboard driver packages and get full keyboard functionality on versions of Ubuntu that the supplier has not installed on this laptop. I am just offering a note of caution about bare bones machines.

Regards

---

