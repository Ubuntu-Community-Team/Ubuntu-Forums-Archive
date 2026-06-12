---
title: "hypothetical WINE compiler"
date: 2009-10-01
forum: Wine
---

### Post by goseph on 2009-10-01
Hello Gents! (and ladies.. well maybe?)

I am sure I am talking crazy here but I am intrigued to find out why. My understanding of WINE is that it acts as a compatibility layer between the GNU API and windows executables, effectively running like an interpreter? Well given that some performance suffers this way, why can't some kind of compiler or even JIT compiler be created that takes windows executables as a "source" and runs the entire thing through a hacked wine interpreter to output something that will run natively on top of a GNU/Linux platform?

All thoughts welcome,

Thankyou all!

---

### Post by Cato2 on 2009-10-01
WINE isn't an interpreter - have a look at the WINE website for details.  

WINE is just a set of libraries used by a program (libraries are .so in Linux, .DLL in Windows) - and in fact because the underlying Linux is often much faster than Windows on the same machine, you sometimes find a Windows program runs faster on WINE+Linux than if you boot into Windows on the same machine.

The only issue with WINE is that not all applications work, but if your apps work OK it's quicker and easier than running Windows in a virtual machine, which is really the only thing that slows down my main Ubuntu box.

---

### Post by Meow27 on 2009-10-01
wine is more like a platform, its like running a  winXP program in Vista, (no i didnt make that up)

---

### Post by doorknob60 on 2009-10-01
You mean something like [http://www.winehq.org/winelib](http://www.winehq.org/winelib) ?

---

### Post by hikaricore on 2009-10-01
> **doorknob60 said:**
> You mean something like [http://www.winehq.org/winelib](http://www.winehq.org/winelib) ?

I think we have a winner ladies and gentlemen.

---

### Post by goseph on 2009-10-02
very interesting, I guess I was thinking of something that would take a .exe rather than platform specific source. Since you can trail through source and pick up on platform specific code to substitute or append a translation, it must be feasible to trawl through a binary and pick out the signature of API calls? (Or maybe it's impossible to differentiate instructions from data in a binary until you actually run it? I really wouldn't know.)

---

### Post by goseph on 2009-10-02
What a detailed reply, thank you for sharing your wisdom. I am very disappointed to hear that Karmic has a lazy boot especially given the promise of improved boot here: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)

Do you suppose that upon release Karmic will be faster? Maybe it is slowed down at the moment because of no -o flags or diagnostic kernel moduels that will be removed from the stable?

---

### Post by hikaricore on 2009-10-02
> **goseph said:**
> What a detailed reply, thank you for sharing your wisdom. I am very disappointed to hear that Karmic has a lazy boot especially given the promise of improved boot here: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-February/000536.html)

Do you suppose that upon release Karmic will be faster? Maybe it is slowed down at the moment because of no -o flags or diagnostic kernel moduels that will be removed from the stable?

I think you posted in the wrong thread.

---

### Post by goseph on 2009-10-02
> **hikaricore said:**
> I think you posted in the wrong thread.
 
woops, yes I meant that to go here: [http://ubuntuforums.org/showthread.php?p=8039717#post8039717](http://ubuntuforums.org/showthread.php?p=8039717#post8039717)
 
Sorry chaps!

---

### Post by scot.mcpherson on 2009-10-02
goseph,
although technically possible, a "decompiling" of executable code, especially Win32/64 executables is called reverse engineering which is most usually a violation of the EULA and loosely speaking is a form of piracy. And that is what you are talking about here, decompling win32.exe and recompiling into an a.out ?

Winelib can often compile from source code we already have if we have all the right support libraries and if we have the license to compile those sources in the non-target environment.

Wine itself though is exactly what is used to run win32 files in Linux, it is an abstraction layer, not an emmulator and not an interpreter.

Really though, even though it is technically possible to do what you want, it is an insurmountable task. Variations in windows libraries, and the countless variations and permutations of hardware, linux systems, kernels, libraries, shells and other environment factors.

Wine pretty much lets us do it easier by "if I get this from win32, do this and return this repsonse to win32"

---

### Post by hikaricore on 2009-10-02
reverse engineering != piracy

You should be more clear with your wording.
Also it's well know that an EULA in many cases will not hold up.

---

### Post by Cato2 on 2009-10-03
> **hikaricore said:**
> reverse engineering != piracy

You should be more clear with your wording.
Also it's well know that an EULA in many cases will not hold up.

Reverse engineering is legal in some jurisdictions, and illegal in others, and there are conditions within which it's legal, e.g. reverse engineering to achieve interoperation with some software is OK in some jurisdictions.

As for the WINE compiler idea - it really is pointless, because **WINE is not an interpreter** as I mentioned above.

It is useful to get native Linux ports sometimes, because you get a native look and feel, but that's often not an option given size of the Windows app market.

---

### Post by asdfoo on 2009-10-04
before you go proposing such crazy things, it would make more sense to work out where the bottleneck is for _one_ particular application you are running, profile that with oprofile and see where the time is spent.

Is it in Wine?  Is it in your video drivers?  Is it in the application?

---

### Post by goseph on 2009-10-06
> **asdfoo said:**
> before you go proposing such crazy things, it would make more sense to work out where the bottleneck is for _one_ particular application you are running, profile that with oprofile and see where the time is spent.

Is it in Wine?  Is it in your video drivers?  Is it in the application?

I was just wondering if this thing was feasible/practical as a point of interest rather than something I actually want to happen. As for the specific one-off application I am mentioning. A friend who plays Guild wars reports much lower frame rates on WINE/Ubuntu than on Windows Vista. I really don't know if that is inferior drivers or WINE itself. I shall implore him to investigate!

---

### Post by asdfoo on 2009-10-06
> **goseph said:**
> I was just wondering if this thing was feasible/practical as a point of interest rather than something I actually want to happen. As for the specific one-off application I am mentioning. A friend who plays Guild wars reports much lower frame rates on Wine/Ubuntu than on Windows Vista. I really don't know if that is inferior drivers or Wine itself. I shall implore him to investigate!

Well, if your friend is using the latest version of Wine,

oprofile is a good place to start, there are examples on the oprofile website which show how to capture data then spit out a report.

The report will show % of time spent in drivers vs parts of Wine.

---

