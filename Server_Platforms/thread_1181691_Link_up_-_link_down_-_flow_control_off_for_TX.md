---
title: "Link up - link down - flow control off for TX"
date: 2009-06-08
forum: Server Platforms
---

### Post by Stoneface on 2009-06-08
I think the Linux iele 2.6.22-15-server [#1 SMP Fri Jul 11 19:54:13 UTC 2008 i686 GNU/Linux]  of a friend of mine has problems. Her Joomla! site went down for a while and when I check dmesg I get:

```
[1181876.269517] tg3: eth0: Link is down.
[1181881.603646] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1181881.603650] tg3: eth0: Flow control is off for TX and off for RX.
[1181890.943101] tg3: eth0: Link is down.
[1181893.078363] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1181893.078366] tg3: eth0: Flow control is off for TX and off for RX.
[1181893.249467] tg3: eth0: Link is down.
[1181895.206173] tg3: eth0: Link is up at 100 Mbps, half duplex.
[1181895.206175] tg3: eth0: Flow control is off for TX and off for RX.
[1181896.992698] tg3: eth0: Link is down.
[1181899.272191] tg3: eth0: Link is up at 10 Mbps, half duplex.
[1181899.272194] tg3: eth0: Flow control is off for TX and off for RX.
[1181905.498792] tg3: eth0: Link is down.
[1181908.413275] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1181908.413278] tg3: eth0: Flow control is off for TX and off for RX.
[1181914.039083] tg3: eth0: Link is down.
[1181915.642769] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1181915.642771] tg3: eth0: Flow control is on for TX and on for RX.
[2995959.757914] tg3: eth0: Link is down.
[2995965.140438] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2995965.140441] tg3: eth0: Flow control is off for TX and off for RX.
[2995974.479895] tg3: eth0: Link is down.
[2995976.615155] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2995976.615158] tg3: eth0: Flow control is off for TX and off for RX.
[2995976.786265] tg3: eth0: Link is down.
[2995978.742474] tg3: eth0: Link is up at 100 Mbps, half duplex.
[2995978.742476] tg3: eth0: Flow control is off for TX and off for RX.
[2995980.529493] tg3: eth0: Link is down.
[2995982.808493] tg3: eth0: Link is up at 10 Mbps, half duplex.
[2995982.808496] tg3: eth0: Flow control is off for TX and off for RX.
[2995989.035749] tg3: eth0: Link is down.
[2995991.950069] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2995991.950072] tg3: eth0: Flow control is off for TX and off for RX.
[2995997.575831] tg3: eth0: Link is down.
[2995999.179072] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2995999.179075] tg3: eth0: Flow control is on for TX and on for RX.
[9599506.004650] tg3: eth0: Link is down.
[9599509.060398] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9599509.060401] tg3: eth0: Flow control is off for TX and off for RX.
[9599518.541323] tg3: eth0: Link is down.
[9599520.679588] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9599520.679591] tg3: eth0: Flow control is off for TX and off for RX.
[9599520.863441] tg3: eth0: Link is down.
[9599522.807688] tg3: eth0: Link is up at 100 Mbps, half duplex.
[9599522.807691] tg3: eth0: Flow control is off for TX and off for RX.
[9599524.654992] tg3: eth0: Link is down.
[9599526.873712] tg3: eth0: Link is up at 10 Mbps, half duplex.
[9599526.873714] tg3: eth0: Flow control is off for TX and off for RX.
[9599533.292226] tg3: eth0: Link is down.
[9599536.296360] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9599536.296363] tg3: eth0: Flow control is off for TX and off for RX.
[9599541.978133] tg3: eth0: Link is down.
[9599543.579651] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9599543.579654] tg3: eth0: Flow control is on for TX and on for RX.
[9851540.113089] tg3: eth0: Link is down.
[9851546.149577] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9851546.149580] tg3: eth0: Flow control is off for TX and off for RX.
[9851555.423914] tg3: eth0: Link is down.
[9851557.559170] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9851557.559172] tg3: eth0: Flow control is off for TX and off for RX.
[9851557.700293] tg3: eth0: Link is down.
[9851559.645350] tg3: eth0: Link is up at 100 Mbps, half duplex.
[9851559.645353] tg3: eth0: Flow control is off for TX and off for RX.
[9851561.443521] tg3: eth0: Link is down.
[9851563.690412] tg3: eth0: Link is up at 10 Mbps, half duplex.
[9851563.690414] tg3: eth0: Flow control is off for TX and off for RX.
[9851569.947800] tg3: eth0: Link is down.
[9851572.880294] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9851572.880296] tg3: eth0: Flow control is off for TX and off for RX.
[9851578.489953] tg3: eth0: Link is down.
[9851580.073644] tg3: eth0: Link is up at 100 Mbps, full duplex.
[9851580.073647] tg3: eth0: Flow control is on for TX and on for RX.
[10211835.978281] TCP: Treason uncloaked! Peer 118.175.179.136:3980/80 shrinks window 2358037307:2358040067. Repaired.
[10542643.839833] tg3: eth0: Link is down.
[10542649.212584] tg3: eth0: Link is up at 100 Mbps, full duplex.
[10542649.212587] tg3: eth0: Flow control is off for TX and off for RX.
[10542658.723404] tg3: eth0: Link is down.
[10542660.882974] tg3: eth0: Link is up at 100 Mbps, full duplex.
[10542660.882977] tg3: eth0: Flow control is off for TX and off for RX.
[10542661.035351] tg3: eth0: Link is down.
[10542662.970669] tg3: eth0: Link is up at 100 Mbps, half duplex.
[10542662.970671] tg3: eth0: Flow control is off for TX and off for RX.
[10542664.826916] tg3: eth0: Link is down.
[10542667.036688] tg3: eth0: Link is up at 10 Mbps, half duplex.
[10542667.036691] tg3: eth0: Flow control is off for TX and off for RX.
[10542673.465673] tg3: eth0: Link is down.
[10542676.427969] tg3: eth0: Link is up at 100 Mbps, full duplex.
[10542676.427972] tg3: eth0: Flow control is off for TX and off for RX.
[10542682.149988] tg3: eth0: Link is down.
[10542683.755342] tg3: eth0: Link is up at 100 Mbps, full duplex.
[10542683.755344] tg3: eth0: Flow control is on for TX and on for RX.
[11313376.766676] Failure registering capabilities with primary security module.
[11993981.754500] tg3: eth0: Link is down.
[11993984.895399] tg3: eth0: Link is up at 100 Mbps, full duplex.
[11993984.895403] tg3: eth0: Flow control is off for TX and off for RX.
[11993994.234848] tg3: eth0: Link is down.
[11993996.391412] tg3: eth0: Link is up at 100 Mbps, full duplex.
[11993996.391414] tg3: eth0: Flow control is off for TX and off for RX.
[11993996.541218] tg3: eth0: Link is down.
[11993998.463675] tg3: eth0: Link is up at 100 Mbps, half duplex.
[11993998.463678] tg3: eth0: Flow control is off for TX and off for RX.
[11994000.284450] tg3: eth0: Link is down.
[11994002.529697] tg3: eth0: Link is up at 10 Mbps, half duplex.
[11994002.529700] tg3: eth0: Flow control is off for TX and off for RX.
[11994008.789707] tg3: eth0: Link is down.
[11994011.689087] tg3: eth0: Link is up at 100 Mbps, full duplex.
[11994011.689090] tg3: eth0: Flow control is off for TX and off for RX.
[11994017.330849] tg3: eth0: Link is down.
[11994018.879329] tg3: eth0: Link is up at 100 Mbps, full duplex.
[11994018.879332] tg3: eth0: Flow control is on for TX and on for RX.
[12702290.764965] TCP: Treason uncloaked! Peer 62.68.66.158:15594/80 shrinks window 963882174:963883218. Repaired.
[15815131.556696] tg3: eth0: Link is down.
[15815136.934872] tg3: eth0: Link is up at 100 Mbps, full duplex.
[15815136.934875] tg3: eth0: Flow control is off for TX and off for RX.
[15815146.210476] tg3: eth0: Link is down.
[15815148.345738] tg3: eth0: Link is up at 100 Mbps, full duplex.
[15815148.345741] tg3: eth0: Flow control is off for TX and off for RX.
[15815148.496865] tg3: eth0: Link is down.
[15815150.461556] tg3: eth0: Link is up at 100 Mbps, half duplex.
[15815150.461559] tg3: eth0: Flow control is off for TX and off for RX.
[15815152.250075] tg3: eth0: Link is down.
[15815154.527579] tg3: eth0: Link is up at 10 Mbps, half duplex.
[15815154.527582] tg3: eth0: Flow control is off for TX and off for RX.
[15815160.754838] tg3: eth0: Link is down.
[15815163.667359] tg3: eth0: Link is up at 100 Mbps, full duplex.
[15815163.667362] tg3: eth0: Flow control is off for TX and off for RX.
[15815169.296557] tg3: eth0: Link is down.
[15815170.877211] tg3: eth0: Link is up at 100 Mbps, full duplex.
[15815170.877213] tg3: eth0: Flow control is on for TX and on for RX.
[16580179.284436] tg3: eth0: Link is down.
[16580184.784617] tg3: eth0: Link is up at 100 Mbps, full duplex.
[16580184.784620] tg3: eth0: Flow control is off for TX and off for RX.
[16580194.124082] tg3: eth0: Link is down.
[16580196.259349] tg3: eth0: Link is up at 100 Mbps, full duplex.
[16580196.259352] tg3: eth0: Flow control is off for TX and off for RX.
[16580196.420453] tg3: eth0: Link is down.
[16580198.335135] tg3: eth0: Link is up at 100 Mbps, half duplex.
[16580198.335137] tg3: eth0: Flow control is off for TX and off for RX.
[16580200.163686] tg3: eth0: Link is down.
[16580202.380199] tg3: eth0: Link is up at 10 Mbps, half duplex.
[16580202.380201] tg3: eth0: Flow control is off for TX and off for RX.
[16580208.669030] tg3: eth0: Link is down.
[16580211.624780] tg3: eth0: Link is up at 100 Mbps, full duplex.
[16580211.624783] tg3: eth0: Flow control is off for TX and off for RX.
[16580217.210132] tg3: eth0: Link is down.
[16580218.794558] tg3: eth0: Link is up at 100 Mbps, full duplex.
[16580218.794561] tg3: eth0: Flow control is on for TX and on for RX.
[735760.039294] tg3: eth0: Link is down.
[735765.417188] tg3: eth0: Link is up at 100 Mbps, full duplex.
[735765.417191] tg3: eth0: Flow control is off for TX and off for RX.
[735774.756651] tg3: eth0: Link is down.
[735776.913207] tg3: eth0: Link is up at 100 Mbps, full duplex.
[735776.913210] tg3: eth0: Flow control is off for TX and off for RX.
[735777.053018] tg3: eth0: Link is down.
[735779.001519] tg3: eth0: Link is up at 100 Mbps, half duplex.
[735779.001521] tg3: eth0: Flow control is off for TX and off for RX.
[735780.796255] tg3: eth0: Link is down.
[735783.067541] tg3: eth0: Link is up at 10 Mbps, half duplex.
[735783.067544] tg3: eth0: Flow control is off for TX and off for RX.
[735789.300700] tg3: eth0: Link is down.
[735792.234672] tg3: eth0: Link is up at 100 Mbps, full duplex.
[735792.234675] tg3: eth0: Flow control is off for TX and off for RX.
[735797.842661] tg3: eth0: Link is down.
[735799.417183] tg3: eth0: Link is up at 100 Mbps, full duplex.
[735799.417186] tg3: eth0: Flow control is on for TX and on for RX.
[1736930.575816] tg3: eth0: Link is down.
[1736935.060365] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1736935.060368] tg3: eth0: Flow control is off for TX and off for RX.
[1736944.486036] tg3: eth0: Link is down.
[1736946.624336] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1736946.624338] tg3: eth0: Flow control is off for TX and off for RX.
[1736946.818289] tg3: eth0: Link is down.
[1736948.744084] tg3: eth0: Link is up at 100 Mbps, half duplex.
[1736948.744087] tg3: eth0: Flow control is off for TX and off for RX.
[1736950.609859] tg3: eth0: Link is down.
[1736952.893943] tg3: eth0: Link is up at 10 Mbps, half duplex.
[1736952.893946] tg3: eth0: Flow control is off for TX and off for RX.
[1736959.246960] tg3: eth0: Link is down.
[1736962.285236] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1736962.285239] tg3: eth0: Flow control is off for TX and off for RX.
[1736967.932816] tg3: eth0: Link is down.
[1736969.526201] tg3: eth0: Link is up at 100 Mbps, full duplex.
[1736969.526204] tg3: eth0: Flow control is on for TX and on for RX.
[2288509.784791] tg3: eth0: Link is down.
[2288557.875940] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2288557.875944] tg3: eth0: Flow control is off for TX and off for RX.
[2288567.148754] tg3: eth0: Link is down.
[2288569.305301] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2288569.305304] tg3: eth0: Flow control is off for TX and off for RX.
[2288569.455116] tg3: eth0: Link is down.
[2288571.413629] tg3: eth0: Link is up at 100 Mbps, half duplex.
[2288571.413632] tg3: eth0: Flow control is off for TX and off for RX.
[2288573.208340] tg3: eth0: Link is down.
[2288575.479652] tg3: eth0: Link is up at 10 Mbps, half duplex.
[2288575.479656] tg3: eth0: Flow control is off for TX and off for RX.
[2288581.713467] tg3: eth0: Link is down.
[2288584.624268] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2288584.624271] tg3: eth0: Flow control is off for TX and off for RX.
[2288590.254707] tg3: eth0: Link is down.
[2288591.850251] tg3: eth0: Link is up at 100 Mbps, full duplex.
[2288591.850254] tg3: eth0: Flow control is on for TX and on for RX.
```

What does this mean and why do you think the server does this? My server knowledge is limited so I am learning as stumble along..

---

### Post by ian dobson on 2009-06-08
Hi,

Looks like a dodgy network cable/screwed up switch or network card.

Linux is just telling you that the network card is loosing it's connection to the network, then getting it back and when it tries to set the link to 100Mbit the connection dies again.

If it's worked up till now then I guess someone has damaged the network cable.

Regards
Ian Dobson

---

### Post by Stoneface on 2009-06-08
Thanks for that answer Ian! Will ask her to check.

---

