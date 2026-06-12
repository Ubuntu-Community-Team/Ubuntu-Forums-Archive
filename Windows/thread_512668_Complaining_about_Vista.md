---
title: "Complaining about Vista"
date: 2007-07-29
forum: Windows
---

### Post by Dennis123 on 2007-07-29
I was very happy with Vista x64 until today(that sound too hard...), when I've discovered just a very little flaw:

```

// Get the IExtractImage interface
IExtractImage* lpExi;
lpShf2->GetUIObjectOf(NULL, 1, (LPCITEMIDLIST*)&pIdl, __uuidof(IExtractIcon), NULL, (void**)&lpExi);
lpShf2->Release();
CoTaskMemFree(pIdl);
// Get the image location
WCHAR Path2[MAX_PATH + 1] = {0};
DWORD dw1 = IEIT_PRIORITY_NORMAL, dw2 = IEIFLAG_QUALITY;
SIZE s1 = { 128, 128 };
lpExi->GetLocation(Path2, MAX_PATH, &dw1, &s1, 32, &dw2); // <- Problem
// Extract the bitmap
HBITMAP hBm;
lpExi->Extract(&hBm);

```

Now let's have a look at the signature of IExtractImage::GetLocation
```

HRESULT GetLocation(
    LPWSTR pszPathBuffer,
    DWORD cchMax, <------- 2. arg is an unsigned long
    DWORD *pdwPriority,
    const SIZE *prgSize,
    DWORD dwRecClrDepth,
    DWORD *pdwFlags
);

But now it becomes bizarre:
When I call the function it tries to access the pseudo-pointer at the location of cchMax!
Really: It tires to dereference an integer, better said MAX_PATH(meaning 260).

Such an error should have been detected, when they've created the os,
the function still works under XP...

```

---

### Post by Wiebelhaus on 2007-07-29
May I ask a question?


Thanks , How do i make my mind understand what your talking about?

---

### Post by darksong on 2007-07-29
I think you are trying to extract something? - Please elabortate. Oh and btw is you are using a 3rd part application in 64bit vista, you will most defiantly have appication compability problems. That why i run 32 bit vista while on 64bit processors, once it becomes more supported i can upgrade for free + postage and packaging.

---

### Post by Dennis123 on 2007-07-29
THe function is from the shell32.dll of windows, it extracts the preview icon of an file and is used inside a 64-Bit program, which I'm currently programming(a kind of photo browser, video preview...)
[IExtractImage]("http://msdn2.microsoft.com/en-us/library/ms645964.aspx")

---

### Post by darksong on 2007-07-29
Thank you for the explianation.

---

### Post by Dennis123 on 2007-07-29
Was this meant sarcastically? :)

It's really a little bit difficulty to explain, because it uses COM, but basically I'm only trying to use the standard windows way to get an image from a file(associated icon or when png... the image), but the operating system makes such a simple mistake...

---

### Post by darksong on 2007-07-29
nope - i meant that truthfully :D

---

