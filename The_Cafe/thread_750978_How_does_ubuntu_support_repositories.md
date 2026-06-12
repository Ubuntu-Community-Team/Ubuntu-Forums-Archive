---
title: "How does ubuntu support repositories"
date: 2008-04-10
forum: The Cafe
---

### Post by tamoneya on 2008-04-10
I have always been curious how ubuntu manages to provide the repositories as a free service. It seems like it would take a huge chunk of bandwidth and would be a very large cost for them.  Also as ubuntu is becoming more and more popular it is only going to become harder for them to support.  Does anyone know how this is done and how they plan on scaling it efficiently.  I wouldnt be surprised if they used a torrent like protocol but it doesnt appear that they are.

---

### Post by billgoldberg on 2008-04-10
> **tamoneya said:**
> I have always been curious how ubuntu manages to provide the repositories as a free service. It seems like it would take a huge chunk of bandwidth and would be a very large cost for them.  Also as ubuntu is becoming more and more popular it is only going to become harder for them to support.  Does anyone know how this is done and how they plan on scaling it efficiently.  I wouldnt be surprised if they used a torrent like protocol but it doesnt appear that they are.

I think canonical provides the repositories.

They make money off ubuntu so they need to have the repo's working.

On how it works, I'm not sure.

Maybe ubuntu (synaptic) downloads it using a ftp sort of protocol directly from canonicals servers?

---

### Post by bonzodog on 2008-04-10
The files are fetched via something very similar to wget using the http protocol.The servers are provided by canonical, with the main ones being in London, UK, which are then mirrored around the world.

---

