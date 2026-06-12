---
title: "KVM GPU Passthrough: One Monitor?"
date: 2016-05-14
forum: Virtualisation
---

### Post by jim_deadlock on 2016-05-14
I'm new to KVM (always used Virtualbox before). I've set up a Win10 guest, it's working nicely, now I want to take the next step and install a 2nd video card and pass it through to my guest. Having done some research I realise this is not for the faint-hearted so I want to double-check something before I start. Will I still be able to run the guest in a window the same way I do now, but with it using the 2nd card?

I was reading something where they were talking about attaching a physical monitor to each card so I just want to make sure this was their choice, not mandatory.

---

### Post by KillerKelvUK on 2016-05-14
Hey jim, think of this as just like a normal PC...you put a GFX card in it and you would normally connect it to a monitor.  If your intentions are for gaming then this is the only way!

The above said you could have a headless Windows guest aka pass your GFX through and then use remote desktop so you can access the guest from your host, very limited use-case here however in my opinion as the graphics/user experience won't warrant having a dedicated GFX card.

---

### Post by jim_deadlock on 2016-05-14
Maybe I'm missing something but if this is the case then surely it's easier to just dual boot rather than have your case stuffed with an unnecessary extra card and 2 monitors cluttering your desk?

---

### Post by KillerKelvUK on 2016-05-14
:-) its personal preference for a good part.  Myself, I have 2 monitors and have my Ubuntu desktop across both, each monitor has multiple inputs so when I start my Windows guest I just change the put of the monitor attached to the passed thru GFX card so I have one Ubuntu and one Windows,  dual-boot is kinda a clunky option in my opinion and definitely not as quick...2 desktops working at once.  Or if you have a single monitor you just change the input and you alternate desktop is their...no booting necessary.  Regards the extra card point that's a fair summary, I choose Intel and just opt for the integrated graphics on my CPU for host output, my GTX 970 is for passthrough only, also don't forget Windows isn't the only alternative to linux.

---

### Post by jim_deadlock on 2016-05-14
Thanks that's a useful summary. I'm not an extreme gamer, I have 2 or 3 Win-only Steam games that refuse to work properly with the virtual video card but my main motivation was the catchup TV on NowTV (total refusal), Channel4 and Channel5 (choppy). I think I'm going to take the easy way out and just buy a NowTV box in the end, cheaper than a video card and has all the catchup TV. I do enjoy a technical challenge now and then but I think the hassle/benefit ratio of setting it up is too much even for me :)

---

### Post by KillerKelvUK on 2016-05-14
Just what this forum is for right so glad you got what you needed from it!

If its of interest you can also pass through any type of PCI card to a virtual machine, I run a DVB server which has a satellite card passed through so I can stream live broadcasts to my HTPC.  Not sure what NowTV provides but ask away if you would like more info.

Best of luck.

---

### Post by MAFoElffen on 2016-05-17
I think the best explanation that explains the why not of this (that I've read) is in the XEN doc's. I'll paraphraze that (because it is still a bit techy), but in essence says that a pass-through needs to have an un-used copy of the Video BIOS to be able to copy it over to a virtualized instance, to be able to use it, Therefore it is not sharable between the host and a VM Guest. 

Xen saya that a GPU (that is unused by the host) can be shared between 4 VM guests. Tesla/Grid cards 4 GPU's per card and the NVidia Grid doc's themselves say that when using Grid, that each  GPU can be shared between 16 clients (4 x 16 = 64 clients, per each Grid card). Even with that, the host cannot be one of those to be able to share a GPU. 

But all other hypervisor doc's that do GPU-passthrough say: one GPU pass-through per dedicated GPU. In fact of matter, most Hypervisor's Doc's say that "Dedicated GPU" actually means and is interchangeable with the term "GPU-passthrough". The same doc's clarify that PCI-passthrough is too general a term to cover the complexities of a GPU-passthrough.

---

