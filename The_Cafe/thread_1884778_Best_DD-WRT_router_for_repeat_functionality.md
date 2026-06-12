---
title: "Best DD-WRT router for repeat functionality"
date: 2011-11-21
forum: The Cafe
---

### Post by ki4jgt on 2011-11-21
Hey guys, I just wanted to know your opinions on the best DD-WRT modem for repeater mode. Thanks.

EDIT: Router LOL

---

### Post by doorknob60 on 2011-11-21
I don't know if it's the "best" (this is the only DD-WRT router I've ever used), but this router works great for me, and is compatible with DD-WRT (I recommend Windows for the initial install of it though, it's much easier that way), plus it's only $35 after mail in rebate: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023) Unless you need 802.11n, that router with DD-WRT is probably one of the better options out there.

---

### Post by ki4jgt on 2011-11-21
> **doorknob60 said:**
> I don't know if it's the "best" (this is the only DD-WRT router I've ever used), but this router works great for me, and is compatible with DD-WRT (I recommend Windows for the initial install of it though, it's much easier that way), plus it's only $35 after mail in rebate: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320023) Unless you need 802.11n, that router with DD-WRT is probably one of the better options out there.

I need N (unfortunately). I'm having to hop signal from one building, into another and then into another building.

---

### Post by CharlesA on 2011-11-22
> **ki4jgt said:**
> I need N (unfortunately). I'm having to hop signal from one building, into another and then into another building.

You can get a signal for about 300m max in open space, 100m max in a building, but it's more then likely going to be less then that, if you want good speed.

Depending on how far the buildings are from each other, you might want to look into a parabolic antenna to send the signal to the AP in the other building.

Why not just run cable? It would be more reliable, albeit more expensive.

---

### Post by ki4jgt on 2011-11-22
> **CharlesA said:**
> You can get a signal for about 300m max in open space, 100m max in a building, but it's more then likely going to be less then that, if you want good speed.

Depending on how far the buildings are from each other, you might want to look into a parabolic antenna to send the signal to the AP in the other building.

Why not just run cable? It would be more reliable, albeit more expensive.

I can't spare the expenses. The buildings form a right triangle. The first and second buildings are right next to one another, about 15 meters apart. The third building is about 50 meters from the second building. The first building to third building would work, the third building is completely brick though, so it blocks all wifi signals from the first building. However, when wifi is moved to the front of the first building, the wifi is received in the third building. The problem is that the first building only has an internet connection in the rear part of the building. Thus, if I place a repeater in the front of the second building, it should be received by the third building as the repeater is both closer to the third building and in the front of the second building.

---

### Post by catlover2 on 2011-11-22
I don't have one, (yet) but this router's specs look pretty nice: [http://www.newegg.com/Product/Product.aspx?Item=N82E16833320038&cm_re=rt-n16-_-33-320-038-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320038&cm_re=rt-n16-_-33-320-038-_-Product)

---

### Post by CharlesA on 2011-11-22
> **ki4jgt said:**
> I can't spare the expenses. The buildings form a right triangle. The first and second buildings are right next to one another, about 15 meters apart. The third building is about 50 meters from the second building. The first building to third building would work, the third building is completely brick though, so it blocks all wifi signals from the first building. However, when wifi is moved to the front of the first building, the wifi is received in the third building. The problem is that the first building only has an internet connection in the rear part of the building. Thus, if I place a repeater in the front of the second building, it should be received by the third building as the repeater is both closer to the third building and in the front of the second building.

Oh nasty. Your best bet would be to place APs in such a way that they overlap, so you have coverage, but you will have to set them up in ["client bridged"]("http://www.dd-wrt.com/wiki/index.php/Client_Bridged") mode, so that they all send data to the main router.

I've not done a set up like that so I am not sure if the APs need to be on the same channel or not.

Are you wanting a different AP in each building (with a different SSID) or all 3 with the same SSID and channel so you can "roam" between them?

---

