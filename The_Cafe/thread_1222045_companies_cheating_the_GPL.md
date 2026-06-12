---
title: "companies cheating the GPL?"
date: 2009-07-24
forum: The Cafe
---

### Post by windows-killer on 2009-07-24
I have seen some non/linux/unix OSes out there that are closed source and are a little bit simmilar to linux "lets say ubuntu"

these OSes are closed sourced, how can a closed sourced software contain open source code?

let me give you a scenario: 

lets say I modify the source code of ubuntu, I change the names of everything in there, I re-design the UI, I mix up other code with it, make it impossible to look like ubuntu and then I closed source it. Can the GLP know that I stole code from them? if yes how can they prove it if they dont have access to the source code?

Please enlighten me, I am seeing some similarities on other OSes, some are popular some are not!

---

### Post by swoll1980 on 2009-07-24
> **windows-killer said:**
> I have seen some non/linux/unix OSes out there that are closed source and are a little bit simmilar to linux "lets say ubuntu"

these OSes are closed sourced, how can a closed sourced software contain open source code?

let me give you a scenario: 

lets say I modify the source code of ubuntu, I change the names of everything in there, I re-design the UI, I mix up other code with it, make it impossible to look like ubuntu and then I closed source it. Can the GLP know that I stole code from them? if yes how can they prove it if they dont have access to the source code?

Please enlighten me, I am seeing some similarities on other OSes, some are popular some are not!

You can only close the source on the changes that you made. For example Ubuntu 9.10 will ship with Ubuntu 1 which is a closed source application.

---

### Post by Viva on 2009-07-24
Companies tried that already and [got sued]("http://en.wikipedia.org/wiki/Gpl-violations.org#Fortinet")

---

### Post by binbash on 2009-07-24
> **swoll1980 said:**
> You can only close the source on the changes that you made. For example Ubuntu 9.10 will ship with Ubuntu 1 which is a closed source application.

As far as i know, Ubuntu One's clients are open sourced but not the back-end

---

### Post by windows-killer on 2009-07-24
how can the GPL tell that you stole code from them if your software is completely closed and re-designed from the ground up? 

please clarify:D

---

### Post by Viva on 2009-07-24
> **windows-killer said:**
> how can the GPL tell that you stole code from them if your software is completely closed and re-designed from the ground up? 

please clarify:D

GPL is not a company, it is a license. The company/programmer that writes the software owns the copyright to the software. Some of them choose Software Freedom Law Center to represent them legally on their behalf. Another website is GPL-Violations.org that works on similar issues and won a few cases already.

---

### Post by windows-killer on 2009-07-24
> **Viva said:**
> GPL is not a company, it is a license. The company/programmer that writes the software owns the copyright to the software. Some of them choose Software Freedom Law Center to represent them legally on their behalf. Another website is GPL-Violations.org that works on similar issues and won a few cases already.

I know GPL is a license, you still didnt answer my question. how can a programmer/ or the GPL prove that I stole code from the programmer if the UI, names and some other codes are modified and closed?

---

### Post by dmizer on 2009-07-24
Most open source code violations are discovered by the developers of the infringed software because their intimate familiarity with their own software allows them to spot unique routines even without access to the source.

---

### Post by Viva on 2009-07-24
> **windows-killer said:**
> I know GPL is a license, you still didnt answer my question. how can a programmer/ or the GPL prove that I stole code from the programmer if the UI, names and some other codes are modified and closed?

You can't prove it in proprietary software either. Employees switch companies and take some of the code with them.

---

### Post by windows-killer on 2009-07-24
thats interesting.

---

### Post by windows-killer on 2009-07-24
> **Viva said:**
> You can't prove it in proprietary software either. Employees switch companies and take some of the code with them.
How about if you develop/copy the code by yourself?
> **dmizer said:**
> Most open source code violations are discovered by the developers of the infringed software because their intimate familiarity with their own software allows them to spot unique routines even without access to the source.

you mean that the devs who stole the original code and completely modify it, can still make mistakes in that code that results in familiarity with the original code?

---

### Post by Grant A. on 2009-07-24
> **windows-killer said:**
> I know GPL is a license, you still didnt answer my question. how can a programmer/ or the GPL prove that I stole code from the programmer if the UI, names and some other codes are modified and closed?

They can tell by using [decompilation]("http://en.wikipedia.org/wiki/Decompilation"). This will effectively show them the source code of the program in question, which they can then compare to the source code of their program. If it's a match, then they have a GPL violation on their hands. If it's not a match, then they could've possibly broken the law in certain jurisdictions. You can read more about its legality [here]("http://en.wikipedia.org/wiki/Decompilation#Legality").

On that note, it is perfectly legal to close source FreeBSD, because the BSD license is not viral. I do have much more respect for the companies that keep it open source, though. One such company that has gained my respect is Apple. Apple kept the source codes of the partly FreeBSD-derived XNU kernel and Darwin operating system open to the public. Unlike Microsoft, who stole BSD code and then used it in Windows NT's TCP/IP stack, without opening the source.

---

### Post by praveesh on 2009-07-24
Is the mobile internet experience closed source? If yes, aren't they violating the GPL

---

### Post by windows-killer on 2009-07-24
> **Grant A. said:**
> They can tell by using [decompilation]("http://en.wikipedia.org/wiki/Decompilation"). This will effectively show them the source code of the program in question, which they can then compare to the source code of their program. If it's a match, then they have a GPL violation on their hands. If it's not a match, then they could've possibly broken the law in certain jurisdictions. You can read more about its legality [here]("http://en.wikipedia.org/wiki/Decompilation#Legality").

On that note, it is perfectly legal to close source FreeBSD, because the BSD license is not viral. I do have much more respect for the companies that keep it open source, though. One such company that has gained my respect is Apple. Apple kept the source codes of the partly FreeBSD-derived XNU kernel and Darwin operating system open to the public. Unlike Microsoft, who stole BSD code and then used it in Windows NT's TCP/IP stack, without opening the source.

so its legal to fork BSD and close it?
Can you license ubuntu under BSD license?

---

### Post by Grant A. on 2009-07-24
> **windows-killer said:**
> so its legal to fork BSD and close it?

Not all BSDs, because some BSDs are, infact, closed, or under a different license. You can legally close source anything that is licensed under the BSD license, though.


EDIT- You cannot re-license Ubuntu under the BSD license, because Ubuntu is under the GPL, which is a viral license. A viral license is a license classification. It means that all derivatives of the product licensed under the license are under the same license. Notable examples are the GNU GPL and CC BY-SA/CC BY-NC-SA.

---

### Post by koenn on 2009-07-24
> **windows-killer said:**
> 
Can you license ubuntu under BSD license?
no

---

### Post by windows-killer on 2009-07-24
very useful info guys! thanks!

---

### Post by 23meg on 2009-07-24
> **Grant A. said:**
> 
EDIT- You cannot re-license Ubuntu under the BSD license, because Ubuntu is under the GPL, which is a viral license. A viral license is a license classification. It means that all derivatives of the product licensed under the license are under the same license. Notable examples are the GNU GPL and CC BY-SA/CC BY-NC-SA.

More accurately, Ubuntu *contains* code under the GPL, as well as other free software licenses, which you can't relicense. The whole of Ubuntu is not under the GPL, or any other single license.

---

### Post by windows-killer on 2009-07-24
> **23meg said:**
> More accurately, Ubuntu *contains* code under the GPL, as well as other free software licenses, which you can't relicense. The whole of Ubuntu is not under the GPL, or any other single license.

Understood! thanks!

---

