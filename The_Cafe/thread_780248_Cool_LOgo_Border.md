---
title: "Cool LOgo Border"
date: 2008-05-03
forum: The Cafe
---

### Post by Tux.Ice on 2008-05-03
Ok go to start.ubuntu.com/8.04 see the logo in the top left corner, how do i make that kind of border in the gimp? i attached a screenshot as well

---

### Post by nabl on 2008-05-03
If you mean the white glow behind the logo, it's not too hard to get. All you have to do is the following.

Open the logo as a new layer, then do an alpha to selection on that layer. Keeping that selection, make a new layer and place it under the logo layer. Then select the new layer and fill the selection with white. You won't be able to see it unless you hide the logo layer, but it will be white if you do so. Then select none and do a Gaussian Blur of about 20-30 on the white layer. That will give you that border. Optionally, you could set that blur layer to Screen or another layer effect if you want it to look different depending on the background.

---

