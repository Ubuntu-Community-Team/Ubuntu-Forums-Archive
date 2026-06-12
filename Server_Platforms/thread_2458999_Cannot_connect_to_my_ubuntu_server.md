---
title: "Cannot connect to my ubuntu server"
date: 2021-03-08
forum: Server Platforms
---

### Post by nitchgamingstudios on 2021-03-08
I get this error ```
ssh: connect to host 192.168.0.254 port 22: Connection refused
``` when I am trying to connect to my server
How do I fix this. The server is on a partition on my C drive. Any fixes?

---

### Post by SeijiSensei on 2021-03-08
> **nitchgamingstudios said:**
> I get this error ```
ssh: connect to host 192.168.0.254 port 22: Connection refused
``` when I am trying to connect to my server
How do I fix this. The server is on a partition on my C drive. Any fixes?
Did you install openssh-server? Is it running? Is the machine firewalled in any way? Are you sure the machine is at that address? Are you using static addressing? DHCP reservations?

---

### Post by ActionParsnip on 2021-03-08
Can you SSH to localhost if you are sat at the server rather than remote? Which OS is the server side running? Which OS is the client running? Can other clients connect OK?

---

### Post by nitchgamingstudios on 2021-03-08
Yes. Open SSH is installed. Windows defender firewall has been turned off and yes, the machine is at the correct address. What do you mean by static addressing?

---

### Post by nitchgamingstudios on 2021-03-08
Let me give it a shot

EDIT: 
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAmkAAABMCAYAAAA2jyB AAAgAElEQVR4Ae2dTat9SXXG83EyyMCBOlGaHggmjd2BdtC0irR0gwNFxTeUJtAiaCA6UDAGacmgJQRUDEhCQCQDgxNfRkoGCWaSuR/hhN8Nv38/rNTeu/Y9 5577v uwWbVrlr1rJdau9Y6te8950/ 9M/eeeqrfdAx0DHQMdAx0DHQMdAxcF0x8Ce9INe1IL0evR4dAx0DHQMdAx0DHQPEwOFF2sff NDpxdde6NO5PqHsGLjiGPiv//6fq1qfb//tm6dPf 7LV6VTJ8mnK0l2jD1d6/lYns9Di7TnPvwXp7/7xZdP3/rZFy662SLzk1//6EVlPpYAaTufzo3tLos0ii3wvd78 39YfTZfee2TN7y/ 4//XOXrWHw6YvFn//bvJ65Lrud9xRjPwFb8X9IPe2XtfZb34u/ln9Xn0jH2lx/88J19yDy0SMPhr7/58ROnaXudfw7/QyjSPvTpD57 5qefvSliobWofOOtT5y4ZvzwtR9 6gbni9957f/xg4E/vJAF37ueee8NL3IdG1FPQeH/zDdfuSm44QOnruuWrBlbZvURa4/taZ92ZR9t4tUxZUBZL2XBRzvXbAZnxofwsD58sAETit9Tl6Pa7332z08/ McfnyiGSB7QH//Tv5zoP0oGOOCxmbqhziSpf/7Xn5846ThSj8baV9T96re/e1I8ER93VUhdOoEaB/cRYw hSPurN752Yu3RFZrP622eZf19F3RWn0vHGD7Df2s23/b5OrxIW1PyrsZIbplA70rObXEpAtSRtoXJK1966cmizhZpzz7/vhss Cmcqk72I4OLIgTZ9MOrfMYoDhiDyg8 fBQKqbO8Wahtyaq6je5n9WHuXtu1Capd oK LEIpytQPG HDd/SjI/ZTqFnszuDM pDCjFjQF/pdfY6ibiQUQyYPCrW//sa3n9h lCxxlON9032F0yX9lYmNdXvairRL lJZ1x7/ UGKtnvEaE 4NlvW9MlYdi3ukuq3NRmp057na7NIIxFzmXBIILRTGRIe/V4WBMlDu55OkAR5RZp8YHmqQBGSyRM ki34yDK50WZexWE Y9AcJxnSr03oYTttgydtcR5UWSRtsJXFHK4swMAnyTOHfmzinn5xkJOy7K UAgK7fbVc/TfC0TYLFTFH9jBmMZQ ox9s7HT HlnOWaNL jjnNrY7V8rapF2sHzZpF/fw5No4N kWzowPlZUxhwyKQa6UR9viis20js3c101iZs6Ix42djYZPh2uncWsbqRsbPEub1owsPl2D5WmAeKNEM7LHvlmclFVPHlJfTm7QwZNLTjGR5au3qh9 RHf0UKdzZaUiWpcqAZH jMfY7P GeGRzn4Q130Tcrbas/gzMQYcjhN sUvf/1EH9aOdUodwHItWXfm5DivvNAJm/zwQ5t5yTezpvoGPWynj8DN9XGdocqaWQvwiTvmEI/YxD394khHtjgG3fIPPFt 1g5knbO3zMTGjM5bPsRmdB1ddd3VCbmj54v 0TVVpJHASMgkN2gtQkhIJFiTLDxVGIUJ88ACh8REsWFyhJ8CBh5lMcY9uOIxZnEGJskUnky84tDHXCg8Fk7qydwc0zZlqYv3zkt9nC8W91xZEIGDrhZL4qafaOe9MitFDhf9 jJ5RjgjvZmz1O9apZ3wa6u27ZGVOi61l/SR/za2O1eK77HDe6gnZxS8xk61Pflpb HM FB7qz74Ffwq0yRekzt8z73 g9NL3/3N6cVv/Pz0npc/fzP3A1/50eljP/njExznuxFW/Nl7khEbEBebORtUJozEYaxuVo77dxzqM8KYkQU ctBFvaDMVdYMncHB99qE3s5xTdjU6SfhuymTmEy0jKELCagmQjbu7DtClvogd3SlX9SXPtqpC33auubnGR6wTcDoZFzqw9RprS0OFLlQ1iZxZmKM9WEeOoHDWrEW3CvftVAWY8xxPeFjzOIMTPxkrFQc5DBXf6kzfczRx7QZ0zZx6KfPe elPmKLxT1XPhfgZHyKm9jKYIz53ied8c Mn2eed Wu6YP WzE2o/OWD40vYxj/e6Wf0Rmd9CuUddGWNTpVpFEU8akfID/918SiEAsQ76WcDFBUiEM/STHv5XGOpxGeQnlPUpXHE6XUBxznyEeCtwjK5GgbPjAyOVZb5IWKa0JNOxyDqjPj BG9aNcCp94nhm3moZP2g1VPXEY48DGv6jiyB1n6YYt/S5b4yB5d2iWVP/3r2KztFq7Y4CUGFD3oz76Uq 2OMyZOzpvF2fIhMYEf5SOe6QNfHZLmJmz/u59/9aYY 8hbfzi9/P3f37Qp1ijaskgjYedpgYlBnNtST/jArxhrG2nymhyyb9QeyWLDY/5I/ghjqW8GB/ xIScGm62br/1ieRrDhp2 sGhT59Hp2lGy1GmLohMXfNAaH9qkziO8WR6KmZyfvsn tTaywFEf6BoOY8ypmPiZhC4O46xH3svjXNfTWPCe JTHNc3CZmtNeb61wTZ4FgtiV1vkzf1hay3UGTvxI7bQZt7IT qlDkm3/AOvPOnX6ufEpD163uVZ0wf9t2JMfcTTH64p/Vs dG5dH/uTbj1fyZvtqSKNJJKTRgnKccYqP2P019c6zpHCU4srihDxMpk6R yaQMGqV8VhjpjgcM8csWk7hz55ofJ4YiIvGJ405Rza8DgXvsSmnffiJ1WW J76eA8vGFmocI9cT98Sb2QP4/rBwsE5lX9LFvOZs3SJK6349kNnbcfWeiUOY9iXfSlX2x33Xkz7Z3G2fOgaim 8b8WCekCfffWrN8UYlPv3f 57Jwo2CjRO05KXtp8g2eTYqHLTrLyjezYzNhw3czDAygThvLWNVB4ofKPEMCPLT hisGEyL/Fn2jM4yBhdVXc39yW5JnBkwoM/R0nlCFlLOuztn/HPDI9xk/KxM4uZHFtq78VBRl0nsOnH/0ty5MnkTR9xL96oSHJe2jVaz9RLHObYBod7 GiLq2zu5YXKs7UWzhHPuchKbPGQn7bY7/w1/8iz5eeZ5125a/qgf7Wh8nO/pfOWD9Wlro/9R9CLFmm1AKsGkKgqj0kL3kymObcmTHFqccApReKQgMWk34QsNjiZLOWFygOlSOJ0i0LIUxCKCsacQxs85yIrsWnnfeLb9kSMuVy PvU1LnxgIMfLgq0WC/Cqmzopx4Ko9vta0KJwjyyx1 iSPsyZtX3Lh/gF36UeFkrIz3byMIe59m3hzPoQPPyJbC7aYG99oFEP6DueeeGmUINm/1qbDcpNum5Ua/P81M3JAxsTF/PFq3PrxljHvYevbqp7ZLG586mbUy2KHfDYYMWfpVs44GIvvsuLoitlYAu82Vfbvo6hP9vyHSHLNQZrdClrlm75B5wtnpkEOqPPXhzsrzGGHP28JnPEc9sibS1 XC eK9voVYuAaou80LRjbS2cow ci6wlPzGW La3/KOMtb1mz/Mu3pI M7ExozNy1nyo/XV97D CXqxIo9iigBkVCxoCD0WF9yYsCzdfbfq6Dz77MvFmYSdWUosB5thmfJSIM lbpDAn8bKNfSRZT67UDx7spx8ecBO73iembQtA8PNSFnwzOOJpe7VHv6dPxc712SNLmWt0SR/mHGU7fku7WAtsAh852p4 pX8UGzM4yQMOPksf0ueFbJ8T2vYndSPNvtu02aCYl4lmBseNPfXwZC77xBpthI4lha8mhr2yxGOzB2/2bz6cV kIZ9Zf2KKPK673np6RBOCtReURsrABPy5d6nIbOvJPxRnxzCTQijO634szijFw8TOFPbqO5MhDIe24a2bR4cnozOvOGudiQo15kr5t msRUG3xtSBzEi/bdS3UGR7s53mBZ RXeJCpvYlLGx u UeeNT9rb9pw271lZAP6Z1E3o3O1s/rQcdeHuLDvKHpIkUYhQoI1yZJovFdRTxZIhpwSkLy48hTIUwwSGWMkM5IqWOKYxOAFk2RaE6 ywKHNfKiJTz2RYRt87sFSltjoywUe4xSNYqUtzJcnC0ltgJc2F3xcyqKNvWDUCx6LPexwDrTqXHGTt7a1HVrHPLnCDsbVHXny7pHlnDW6pM Rtut77MAmi7 MQ21l/Y0f/aH MzjOWfMhcYQu BJM9EldlAdlg2SjqX8rlDxrbTau3PzdWHLjWpvPmBs7urCZogubuxt43aTYCBmjIEFOvu4ACww3Z3i93yNLbPC5sBOZmTC37GJ8BsfXH8igjb5Q7YbSp920sXMkH170BIvkVXmOlFWxb3M/458ZHuzlSh3ww544ZO4MzlaMgaOfWYPUP58ziwVkoicFCTqzvtrBmoMBL5g F2mXssChXeOHe31hG3ww6FeW2OjLBR7jPJfGYtrCfHnyudAGeGlzwcelLKkxLS7UsRn/aPuSn4/cW0Y2YFuuxYzO2sq8JR/iA3UnLuRNP un29BDijQTDEmmXqkUCY8iK3lqQiJhmTgpWmpRQsJWngkNmsUDMkeyLEYsBphjmznco5s6pyxkWizAozwTsTZZaIkBxWb4aGMvMknO4MmnTeIkhcfCQX6pOukncLgcX6PaDq18nDBlETOya4 sij 6X9LnSNvTr7QpxEb2s04Zq8QYvOo9gzPjQ23Gl9hp8a cpDOflpO/ttnATS5sWG4olW/rnk2IjRYMNm43qLoJgsNYysyN3aTBvHqpw4wsi1cxbmvXLA7JxoSlTJM1 tonHSU87RMH2fYlPVJW4t6mPeOfGZ6ZBDqj3wzOTIwha RnknjqkbFIjDEnx4l15VmsQZmXfCNZxo FGXNsM9e4EidlIXP0DM6sBfFn7GEvMinywFOWlL6lZ1kd3RdG/oFnZHv6OX187t6CX9QdyvNY1yLljXSe8aEysCP9QyHt2Dl0s0g7B7zn/t rLAookjonKiRu/CJtH739uq99cTlfsGG1vy/n7/Z1 /oaY4Ciib2AD4C 7pVeo76PUacu0uJvgu4yADh584SQgm32tOsudWrsx5s4ukh7vGvfz32vfcZAniaxL9QTqOTt9uVjp4u0CxVpBjevt7jWXmvJ2/TyD0T7vH3eMdAx8BhjgFedvu58jPZfq81dpF24SLvWQGi9OjF1DHQMdAx0DHQMXFcMdJHWRVr/bVLHQMdAx0DHQMdAx8AVxkAXaVe4KP1J5ro yfR69Hp0DHQMdAx0DNxHDHSR1kVaf3rqGOgY6BjoGOgY6Bi4whg4vEjzizvvo Jsmf1Jp2NgLgb6vzvn/NTx1H7qGOgYuM8YOLRI84tV aqJSxrFV1r45bKXlNuy uF9qDHQRVrH7kON3da7Y/cxxcChRRqO41vZOU27pBMfQpHGF9ryrf3oeu639/tN P6KQfqa719Dhhey4PPLc/1VBccr9dv3R9 WX9d1S1bqtdSe1cf5e2xP27Qr 2gv/eJA/cUK5OYHgRmcGR/Cw/r4HXpQfnlAe4 kfEkl3/jvt4JD Ubt/vLKTnpHxlljdTx1DBwXA4cXafexOCTMTKD3ocOaTAoEdaRtYZI/iUXBM/MFt3y/GljwUoBVufYjg4siRH54lc8YxQFjUPn9/jZ/iol 5sibhdqWrKrb6H5WH butV2boNqlL jDRosjf1YLOdgIH76jX/sp1Cx2Z3BmfYgO/lwYeoENHfnrnD6 tJITNH9eyi xzJ9lOQe/5x63Mbcv25cdAx0DxMBmkUYi5jLhkEBoZwCZWBgzeeW47Xo6QRLM36 EDywTJ0VIJk/GSbbogxyTG 2a1LhnPmPQHCfp0q9N6GE7bYMHWervPKh9JO2UxRyuLMDAp8hhDv3YxD394uhn75coBQR2 2q5 m Eo20WKmKP7GHMYih9Rj/YWRjukaXMNbqkj3NuY7tzpaxN2sX6YZN2cQ9Pro1zk27hzPhQWRlzyKAY5Ep5tC2u MLJOjZzzzeJ 23i57zu5OSNAi9/pw68WuwlD7zcqyc2MIeL37hjrid8/r6nv0dYcf09vTwBPFeWejXtxNgx0DFwTTEwVaSRwEjIJDdoLUJISCRYkyw81UgKE aBBQ6JiWLD5Ag/BQw8ymKMe3DFY8ziDEySKTyZeMWhj7lQeCyc1JO5OaZtylIX752X jhfLO65siACB10tlsRNP9HOe2VWihwu vVl8oxwRnozZ6nftUo74ddWbdsjK3Vcai/pI/9tbHeuFN9jh/dQT84oeI2danvy097CmfGh9lZ98Cv4VabFSS1a4Hvu9R cXvrub04vfuPnp/e8/PmbuR/4yo9OH/vJH5/gON8CqeLP3lMQWVzR9uKHmcVAR3gYQ55z1J0Ci35 RNnikd8RpEBjHmNgUdzVHyqmmMu o2Spe9NO0h0DHQPXEgNTRRpFEZ/6UdpP/zWxaJAFiPdSTgYoKsShn6SY9/I4x9MIT6G8J6nK44lS6gOOc QjwVsEZXK0DR8YmRyrLfJCxTWhph2OQdWZcfyIXrRrgVPvE8M289BJ 8GqJy4jHPiYV3Uc2YMs/bDFvyVLfGSPLu2Syp/ dWzWdgtXbPASA4oe9GdfytV2xxkTJ fN4mz5kJjAj/IRz/SBrw5JLV6y793Pv3pTjH3krT cXv7 72/aFGsUbVmkURhRFFEEcVkwJdZMm6KK XmSVechh6Iw ymsPMmzXyxOzeij0AOboo57izZljU7XjpKlTk07QXcMdAxcSwxMFWkkkVR4lKAcZ6zyM0Z/fa3jHCk8tbiiCBEvk6lzxK4JFKx6VRzmiAkO98wRm7Zz6JMXKo8nJvKC4UlTzqENj3PhS2zaeS9 UmWJ76mP9/CCkYUK98j19C3xRvYwrh8sHJxT bdkMZ85S5e40opvP3TWdmytV Iwhn3Zl3K13XHvxbR/FmfLh66h Mb7ViyoB/TZV796U4xBuX//5753omCjQOM0LXlpe/JEMUSBYwFU ZbuOfFiLhdFFgVVnqIxz/FKl4q0JVkWZciEx398SP4qw/u9shKz252kOwY6Bq4hBi5apNUCrDqARFV5TFrwZjLNuTVhilOLA04pEocELCb9JmSxwclkKS9UHihFEqdbFEKeglBUMOYc2uA5F1mJTTvvE9 2J2LM5fL1qa9x4QMDOV4WbLVYgFfd1Ek5FkS139eCFoV7ZIm9Rpf0Yc6s7Vs xC/4LvWwUEJ tpOHOcy1bwtn1ofg4U9kc9EGe sDjXpA3/HMCzeFGjT719oUMpzKQeuJ19o8xyjK Bs5Tsf8WzILKXjERUZenpiJ40ma9yPKK091zLa8R8oSs2kn6I6BjoFriIGLFWkUWxQwo2JBR8BDUeG9CcvCzVebvu6Dz75MvFnYiZXUYoA5thkfJeJM hYpzEm8bGMfSdaTK/WDB/vphwfcxK73iWnbAhD8vJQF3wyOeNpe7dHv6VOxc332yFLmGl3ShzlH2Y7f0i7WApvAR462p0/pH8XGDE7ygIPP0of0eSHb54S2/UlHrztzfLZNYQMvJ2n1xGkWQz5O4sDLvxObxZ0p0jw981VoFoN7bJiRpU1N347L9kX7omPg/mLgkCKNQoQEa5Il0Xjv4nqyQDLklIDkxZWnQJ5ikMgYI5mRVMESxyQGL5gk05p4lQUObeZDTXzqiQzb4HMPlrLERl8u8BinaBQrbWG PFlIagO8tLng41IWbewFo17wWOxhh3OgVeeKm7y1re3QOubJFXYwru7Ik3ePLOes0SV9jrRd32MHNln8ZRxqK tv/OgP9Z/Bcc6aD4kjdMGXYKJP6qI8qH/4f87fkvmH/BRV/jG/f/ VstbaFE3M8bL44WTNeb4SZYw2xSXU16JQ ijm0IV2PWUTy IMLE7t7JceKUvMpveXlNr37fuOgbdj4JAizQRDkqlXOpuER5GVPDUhkbBMnBQttSghYSvPhAbN4gGZI1kWIxYDzLHNHO7RTZ1TFjItFuBRnolYmyy0xIBiM3y0sReZJGfw5NMmcZLCY Egv1Sd9BM4XI6vUW2HVj5OmLKIGdm1R1bFH90v6XOk7elX2hRiI/tZp4xVYgxe9Z7BmfGhNuNL7LT4V07Sc7 CgyKP14UURVy09xZo6GOxuIVD8WQRJq8ngci1T0oRlvZmWxxfe YY7SNlVey fzthtC/aFx0Dl42BzSKtF T8BaGAIqlzokLixqfS9u/5/m0f7vchhVH7bb/f2mfts46BjoFLxkAXafE3QXfpeE7ePCGkYJs97bpLnRr78W42XaQ93rXv577XvmPg4cRAF2kXKtJ8KHi9xbX2Wkvepg/nQeq16rXqGOgY6BjoGDg6BrpIu3CRdvQCNl5vCh0DHQMdAx0DHQNPZwx0kdZFWv9tUsdAx0DHQMdAx0DHwBXGQBdpV7go/Yno6fxE1Ova69ox0DHQMdAxsCcGukjrIq0/PXUMdAx0DHQMdAx0DFxhDHSRdoWLsqfKbt7 VNYx0DHw2GOA7xD0O/geuy/a/qdrP7hYkcYXVa59WWUH1lxg U3t5/rrKJwtPS697ufaxUbvl6tCb/Nlr1s 2TM q89D8/MeHxzFe25sHKVH4xy71/FLFTyro1 jeOi Zv/JL6Be lWOS9t5DXvjpW2 L3ldpD2wkzS/qf3cgDkKZ0uPSxcP59rF71BSGFkcgbdl412Oz rz0Px8lz5bwj43NsAlSfIbpRbyJFB 7SBlzvAk/7ltYrXqdN9xe65NzN zXtifP0t2hPz7xtB nm3aXOwH960X8rtIm/ugccRadZHWRdqdPvQPuXi4to1oTZ H7OcjNrIZDJPeDO8SD6c1/EQVv5 axRGndM6Z4ZH3XOrvlqITbXTip7PQIXU6V859zD9ive5D76Nk8gGAdT0K70ictb3oSDmN9c7TZpFG5c7DkkeuLFD yPMMj0mEH2dmPhft0SKc xuFYNbf8uOTVj0qxi42M3QZfSKe0XmGB33Sh8jivtq pjP8 q3SEVbF9n4PDrxr/hFzje7xz5qsrRjbY9eavjmGn9d8O OftTVFlid2xiAJdunT8po D9HPI51H9q/5Of3HM86 ZBy5vxwZG7Xw4Z51yVOcGR7j7Ny9zkReY6ber/kQXUZrof/UdYYHXmSZL 5yr6vrin7qmvQI2xNv1J6JQ fN AfeteedsbRX VDlbO2Z8m3pQzwjC5k8Wzxja7qJ2/SY07bNIs0HgQ2QtlduRDM8LDIPLJswgQRlobPYc1HXxuRZoyRGsN0g2GwILu6dZ6ChF/ozxpwMcnWWB1p1nuFRFnLA119p 5bO Dv9Rtsr10L7lugsjjpr 8g/SzKyX/ srfuMLH22FIezdqVuW23WGrkjvhmdt9YUXPRGBhe2IROfjWSu6fMQ/azO2J3PRRYHW34mETGXEwfwuPA7GPiLsbuIDdeHD37IySLNMekazzl7HbYhGx8pa0S3fMgc1wJKLEIr9gyPssDINU0dt56L2fWSTz gX7VffbRrtI/N2FVx6/1MHDJHfZb8U21y38TGPGRgbdJefQBVN2TAt7RnzugDD3Iszlg79ynwldX0mIJs5MfNIo0FYqHrJ7MEm VhoXMeuEsLncGWc2babNg8jKkzAZ738ojHw4E PBT2GZzOg1adZ3iQlbjgE jMVZb6KIv qjN9PnjOuy3dwlEf8Uf cWyN6p/kqT6ckQUO89I/iWl7yy75ZmjVM fM6CxP6jxa08T1ZCXnOL6mz0P080hnnovcJ/ShPliKQ PDRCZf7i9Hxob6iIk8 yrd4rntXjdKzFU29zM dC2MO2iNtxkeZN3HXoeu6FftP8r2irt0vxWHW/4xVrCnXmlftXcUC rimo503tLH5yg/hPCMIR9dR5jdd2zBtlmk anHoGBh6oY0w0PAZJCxkHe10ODmp/FR0MBTNxMCNnWc0XmGB1mjK2XN6IwdPsQjm/b0beHM GdG3qx/ttZiJsaO9A9Y GBpI5rxz8ya8iwRq/qJGGTeKHGv6eP8XJPKz/01 Xmkc43LGZ2xGSx40/7arth1fO89yYqCcm2vmeHZK1f UWJ2LOmMD0drwbyM/xke5owu5qoT42s k2/PeoGZMsSgfyvmZ wSb4uChcwlPsZG15Lu6f/EBCPnjGJhZs8c6ZLYI1z0gGdJt9Sz2 cXbJtFGk4mkVBJ ymXBSIAcgG2eI58EFLuqI1 9cGsfCOeuyzS0IeAz8tP/eg20qfqzP2ejWs0374tnJE 1T9irdGZdZ VtRVj6LFl15qudQy9ljaiGZ1HPCmDT7gkeU59kcNFnDCPOEle2mv6PEQ/j3Su6zfy4SgOwYK3 izvK3aO7W2zPqwdcpfmzvAszZ3pBx b81XiaN6MD0drwTx8JuYMj7LQLa 73uuQO1oL9dEGaI2fGbty/lobLGQu8ahP oZ2 se58Kb/7YcylvaCQR80 bb2zC19lnDXdEv53b5QkZaO9hicgi37sz3i2fsg1GBL/K02DyEb6NYxL8lRLILZgLVvRucZnropiJ90Rmf4TTTom/P3trdw0GfLPzMyZ/2zV9Yoxo70D1g1HtLeGf9sreloA/RvVkbxv6bPQ/QzOvOcpl8pUrNvxs/MBwv/JFZtb8V85R/dE3fiLJ0GzfAk9mitc3ytja94dh77XsfaEwPVVzPxM/PsVNyl 604RJ RniM8bCLWlsYSxz TWIul0Z65pQ/FI3r0687zi63ROs70bZ6ksRERKF4GYS7aDA/zMqhQbikIPU3Y oS4ZKDHvGxgqVvimQzRCdvY6NAng3xG5xke9YGXNjKgWWjJs6Yz9vrQoK9rkmux5JPav4Uz45 KObqf8c MrFxH7Aa3bh7I37JrpONSHxsYMpQNlXdG5601VVdPWcHkww8y6cv4QO6aPg/Rz hMHGMzzwTrqu2zfsZHzNU3tPGr85Pq73OeHZ5PdFRn5Hkpa4ZH3nP3OuMQ 2mjC3GHL5UhD/6m/2nZ61hPfc a4APvj7ZdvCU6G4fuCawFbderPuvIwaZcx3 pDRUAAApISURBVJTtPsGexAWez45Y7ltgcMmT WJGH/xKTBNH8Ct7SbfUs9vnF3ebRZqbCAHA5QaXzp/hIUC4ct5SEBJEjBHAyb nTTC5cas7QZYYBJkbKnYxJ8dndJ7hAXOkT7VvxFN1Bos N1ps46FJvWfbWzhb/pmRM ufLVkzMaY W3bJt0VJAunnLNKYu6UzPFtrmhjEq4XE6NlY0 ch lmd8YHPKOtcT4XSR/U5zbligLu0tufGhjJGVJmjMfvkkR6x17GPmDiVU32w5kN0cS3UCwoW8 yb4YF3FPN3sdehj/ZWqs7QI2xPvFF7TxzO AcZ1f8pl71A 6GjfWN2z9zSJ2VZrEEzNlK3bp9fmKUPN4u0ZO72sc5vf7Y/H3MMjJL Y/ZH2977QcdAx0CNgS7SHtgvDtQF7Pt qB9qDHSR1rH7UGO39e7YvVQMdJHWRdqT1xmXCrqW0xscMdBFWsdB7wUdAx0D6zHQRVoXaV2kdQx0DHQMdAx0DHQMXGEMdJF2hYvSnyzWP1m0f 7PP6fTqTfy3jM6BjoGOgYuFANdpF3I0V1Y3F9h0b4/zvddpB3ny47L9mXHQMfAVgx0kdZFWn8i6hiYjoEu0jqpbCWVHu8Y6Rg4LgYOL9I /saHTi9sL0pt Ledxiti/bl7MxwHcwzfImXxdpHWMZD93ueOgYuNsYOLRIe 7Df3H6u198 fStn33hVgngtouNzE9 /aMXlXlbXXve3QZ0 3fOv12kzfmp46n91DHQMXCfMXBokYYhr7/58ROnaZc06iEUaR/69AdPf/PTz94UsdBaVL7x1idOXDN9oPP3WD88XvvPb/ MHAH17Igu9dz7z3hhe5jo2op6Dwf abr9wU3PCBU9d1S9aMLbP6iLXH9rRPu7KPNvHqmDKgrJey4KOdazaDM NDeFgfPtiACcXvqctRbb7Jn19N8Fc2oKNv F T1ydpnbDW4qPHOj46Bo6NgcOLtPtYIJJbJtD70GFNJkWAOtK2MHnlSy89ScazRdqzz7/vBgt Cqcq135kcFGEIJt eJXPGMUBY1D5wYePQiF1ljcLtS1ZVbfR/aw zN1ruzZBtUtf0JdFKEWZ mEjfPiOfnTEfgo1i90ZnFkfUpgRC/pCv6vPUdSfrvGniPy5HH4qaVZGF2nHbsCzfm9nvHwOOMgc0ijUTMZcIhgdDOgCHh0e9lQZA8tOvpBEmQV6TJB5anChQhmTzhI9mCjyyTG23mVRzmMwbNcZIh/dqEHrbTNnjSFudBlUXSBltZzOHKAgx8kjxz6Mcm7ukXBzkpy/5KKSCw21fL1X8jHG2zUBFzZA9jFkPpM/rBxk7n75HlnDW6pI9zbmO7c6WsTdrF mGTdnEPT66Nc5Nu4cz4UFkZc8igGORKebQtrurvIFa pfv88th 3fk4N/yl2Oj joeOgeuMgakijQRGQia5QWsRQkIiwZpk4akLTmHCPLDAITFRbJgc4aeAgUdZjHEPrniMWZyBSTKFJxOvOPQxFwqPhZN6MjfHtE1Z6uK981If54vFPVcWROCgq8WSuOkn2nmvzEqRw0W/vkyeEc5Ib Ys9btWaSf82qpte2SljkvtJX3kv43tzpXie zwHurJGQWvsVNtT37aWzgzPtTeqg9 Bb/K9AeTRydfz73 g9NL3/3N6cVv/Pz0npc/fzP3A1/50eljP/njExznU R1kXadG3Jd877vdeoYeNwxMFWkURTxqZ9g8dN/TSwGkgWI91JOBigqxKGfpJj38jjH0whPobwnqcrjiVLqA45z5CPBWwRlcrQNHxiZHKst8kLFNaGmHY5B1Zlx/IhetGuBU 8Twzbz0En7waonLiMc JhXdRzZgyz9sMW/JUt8ZI8u7ZLKn/51bNZ2C1ds8BIDih70Z1/K1XbHGRMn583ibPmQmMCP8hHP9IGvDklHp2jvfv7Vm2LsI2/94fTy939/06ZYo2jLIo2/SfvFL399U6BRpI2KvZQ1avfrzsedMEYx0X0dEx0DdxcDU0UaSSQXYZSgHGes8jNGf32t4xwpPLW4oggRL5Opc8SuCRSselUc5ogJDvfMEZu2c iTFyqPJybyguFJU86hDY9z4Uts2nkvflJlie pj/fwgpGFCvfI9fQt8Ub2MK4fLBycU/m3ZDGfOUuXuNKKbz901nZsrVfiMIZ92Zdytd1x78W0fxZny4euofjG 1YsqAf02Ve/elOMQbl// e d6Jgo0DjNC15aVOcUaRxUbRRvFWepfsu0u5uM17yefe3zzsGHm8MXLRIqwVYDTwSVeUxacGbyTTn1oQpTi0OOKVIHBKwmPSbkMUGJ5OlvFB5oBRJnG5RCHkKQlHBmHNog dcZCU27bxPfNueiDGXy9envsaFDwzkeFmw1WIBXnVTJ VYENV XwtaFO6RJfYaXdKHObO2b/kQv C71MNCCfnZTh7mMNe LZxZH4KHP5HNRRvsrQ806gF9xzMv3BRq0Oxfa1Og dqT16BrvDnWRdrjTRYZB93uOOgYuEwMXKxIo9iigBkVCy42PBQV3puwLNx8tenrPvjsy8SbhZ1YSS0GmGOb8VEizqRvkcKcxMs29pFkPblSP3iwn354wE3sep Yti0Awc9LWfDN4Iin7dUe/Z4 FTvXZ48sZa7RJX2Yc5Tt C3tYi2wCXzkaHv6lP5RbMzgJA84 Cx9SJ8Xsn1OaNufdPS6M8dn2xRp8HKSxj8UzM7rIu3t9Zr1WfO1zzoGOgZuGwOHFGkUIiRYkyyJxnsV82SBZMgpAcmLK0 BPMUgkTFGMiOpgiWOSQxeMEmmNfEqCxzazIea NQTGbbB5x4sZYmNvlzgMU7RKFbawnx5spDUBnhpc8HHpSza2AtGveCx2MMO50CrzhU3eWtb26F1zJMr7GBc3ZEn7x5ZzlmjS/ocabu xw5ssvjLONRW1t/40R/qP4PjnDUfEkfogi/BRJ/URXlQ//D/Nn9LxnyKMb52wxM0v5IDmnLW2l2kdbJZi48e6/joGDg2Bg4p0kwwJJl65YKR8CiykqcmJBKWiZOipRYlJGzlmdCgWTwgcyTLYsRigDm2mcM9uqlzykKmxQI8yjMRa5OFlhhQbIaPNvYik QMnnzaJE5SeCwc5Jeqk34Ch8vxNart0MrHCVMWMSO79siq KP7JX2OtD39SptCbGQ/65SxSozBq94zODM 1GZ8iZ0W/8pJeu5XcFDk/eq3v3vy92i09xRo6NJF2rEbcK5vt9u3HQMdAzUGNou0OqHv9wcRBRRJnRMVEjc lLY/9/uzfXa z3zdudeXXaSd7/u9Pm/ 9nnHwOONgS7S4m C7vJB4OTNE0IKttnTrrvUqbEf74PfRdrjXft 7nvtOwYeTgx0kXahIs2HgtdbXGuvteRt nAepMeyVn2S1jH5WGK97exYv4YY6CLtwkXaNSx669Cbz21joIu0jp3bxk7P69jpGNgfA12kdZH25I/h wHa/wC1z9pnHQMdAx0DHQN3FQP/Czvw1WCazRu8AAAAAElFTkSuQmCC[/IMG]
I still get the same error

```
nicodemus@LAPTOP-TAFDGDO9:~$ alias server="ssh nicodemus@localhost"
nicodemus@LAPTOP-TAFDGDO9:~$ server
ssh: connect to host localhost port 22: Connection refused
```

---

### Post by nitchgamingstudios on 2021-03-08
When I run ipconfig in my CMD:

```
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . :----------------------
   IPv4 Address. . . . . . . . . . . : 192.168.0.254
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1
```

---

### Post by nitchgamingstudios on 2021-03-08
I can't access the sshd config file?
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAhwAAAAoCAYAAAC1iiPuAAAUNElEQVR4Ae2dMa8sTXGG TkEhA4JHJIROHRCQGiJgMgBkiPLAREB0Sc5QcgJEgmWJQsR2HJiiwjJgS2R8D O9XzwoFflnuma3dm9s2c7GHVPT3XVW1VvdffMOffcb3zzW3/xsa4Vg8WBxYHFgcWBxYHFgUdy4BuPVL50L/IuDiwOLA4sDiwOLA7AgXXgWF941heuxYHFgcWBxYHFgYdzYB04FskeTrLP8Hbzo7/7 49//c2/f3z7L7/zMvG6F/NPfvrVxw9  Lcv4  r8 zefJ3t/8LzXl8lnlHvlztwfPev/notcusQdLlN7j9/ 7uPX/3Lr/ Mi8MH19mL/Jn6KuYjur/3/b/5 N/f/ Hjd//9P0/1EZtf/ePPn2rzSFweKXtrvh61Zt6KZxajW2vnanheiavUFPEDMxf1nXl6Vr1f7sBBYAhIBqP2OXkbPNq6QB0h9L/9x399be8Xv/zn/2cTPSaIFlvI ZYr1pTJvm HyP/sn37x9eKtHk6T6dfMVspu9bt4nH/E95FfOUafDVmftUFLvrSFHP3MWUdPJ4bIkB82SXTSEvfEcksf/OhL345w7Bab984ZYT6qk3xWnh7VcVSeOCc3js5/hjz4yD 24ASY77V7T76s 3sx5Px78KSeUf W2rkaHvx6Ba6CU34Qd/pc7mGZn2fU 8sdOCxwgkbfYP7Dj3/y56LvEpo3A0iDPIeJDD59x00SCVGe59rnORsdz2iVRz9ybHqSkznK5mI s1Wxje67eJh71Hd9otUvY8FYHqhYHMSHj8gRO8b1n0OHpO/o6caQQwZcMBbGXTy3tOQGvDmXMa4cu1J/hPlK LawnJGvLd1njcN3c 9GeK/ue/IFHuJ2L4acfw e1DPqo9v4jZ6Pxq6GB4yvwFVwsrfV9WsU42eM7R44WLQJKhcbBgu5b4/1zRHS wwHc9PRkT0Zi0Z72fJMHeBgw YePNjhnnFluoRmMwSzn5PqZ6aRHjc N11tGitax2jd2NMHxtGdh5wjtlL/Vn8Lj/K3 O5cW3KUfnGAwCf94l7uOGfUzvR0YqityksKbVRsHoRqvio uZEHWmTMl3zAh2obOeKzVRfmSB1w2H7VhR7iih3ajPuZmNGLDS/8rPq5p 6Iq3Jgr/Wz5zs6yCv60UGMiDH96hv3W753Y4je9MV5mX84lLb0zdzzHHl8xXf6rD1gSz2jeO2NbXGMOYmn5p1nYqwtz9JmJ1/Kb GZxYf5HZlu7VwJT5erYt5rO7kgf1vrBrqPxBBuVD6Ir3Ioa0SZke9g29LpvFG7e CwwCguHSRYLooWmQsFMoBwcfA5hmcyOGUBEyD6XjwTPM8SA/diU6beO15bFg4uxmsxMzbSAybxpb6tcbCO5E20vh2xlXa3 lt4lL/Fd fa4lclnRs5i5Y5B4tzRu1MTyeG lvxEFf0V7t ZXIzqc 9d0Px3ha9cIbn2B7p039kR3UhZnIhH5hTMasHGeakrHiynWEWj3YyBtah2JBJ3fTNhzXDesACxL2yYtYWz2od8MyDBjqJQ WCerZ8F cshuhNX5xHK2bjqi7uuaxR56BrdKnnaLuVr5nv5krugc9LzGDp5Csxb GZxQcdHRnyMKudq HpcDUxb/U7uTDv2CSeW7XDuDK0cJK52JYbcpacyo18Mahy6KnYGcs61RbYquzsfvfA4WQNCBSQOKdBDiQ4r7zPcdKxjgyyEtZ52aqXgxABQD998HEpW 8dz5Z5 MAGyTi6wJgyIz3IMY/5KWtiaXNcf2byM1vqx/boSpv0la94eNb1nZyCP6 0Aw6e5Vja1Xef82ykq6tnFkM4QRyVg6 MoV8M2Y5ik8/lW/URGeygO WrHzPOGyv020dfjRt6spaQYVMEQ9qn38FsfOTByD904c/Ihn6pB1linffKiE9c uG99aeOUQydo6703bjNYlh9cR6tevEVufTDZ9kiZ8w4bI1ilPJ7feOgvpTt5p254M652TcX6VfNl/J7eDrx6crMaudKeIzJjKti3ms7uVBGPdrPOiDOxNCc0mbtyAnG6rXFV TqM22f4Tv HDpwGIDaAjSDwXOCluA7MswzUNUG9y4S9NHnYsGctEU/70e6PGkSUJ57qvSeMXTkpss9dlnwqk6xicnn iMxHK/yM1vMZ87WpV7bqt9x2q7v Fqv1MMz/MuxtKvvPvdenY539cxiaA7VLwdnXBBHbcGbRZ3P0Vn1Vj 436sLY4Ud 9gwTtrTn9pW 869B7M2abE3ssF4/ZFPznNux3f8zrnoxn/Hqs/ei8u4dWLoHHQ7L 1bF9hAFp25HoiJ LoAIzeLhfNGLTa28qWvtU0/0IkOZEb6GeNZF Menk58OjLgrz6AEdvVhyvgGXHFuI4wVx/yvpMLZPZqB31HYrgV28RFH7malzN9x8bbHjhIqImANBQk936SMqmMeXn4qBsfsluJsQBzYUOeBQu9LmgkWju0e7aYP7u28DCv63slX7UJzlpwbvrYz37OZQ5zHZvp6cYQfcQT21z00d1dbMVDS47ZCGrhK9MpeGzX R6C0GOOiId9xkfxQY9 2frFUUxnYFYXLfhHHBj5lfOc2/EdX3IuupNT2tJnW33n3jn20TeKYfqiLG3ahzPUJi8V5B/d8A8Z5zA2ulJPpz/LFzY6ea  VtvqqeP1foYH b34qG8m06kddF0Fj3mvXCGuyVX932s7uRjJ5LqB/m4Mke3iRC5rhLln o6 Uw4cBIMNEoVcLvS54HRkmGvxoEN9tiwyBIV7FgMWBUhZg1/vnZ tiwn68sqvFx096txKjLGoxER3xuyILW3utVt4mHOW78Qt/SIX IR 7Oh7xpRxcyz rp60xdwaQ/XRYhvOgWXEJWTqApLzPSxtzR3lq/ox47w5wi/7YKjxQQ/2Et ofwbm1Is/I7vGlXynfPZnvlvLfilgrmOZ55nvxm0Ww qLB/49DuAf8 Qv99pjPn345aEg/e/0Z/ma a4N bLF1U6 0DXDoz3bGh/Hsx3JdGoHHVfBIy9nXE2/t/qdXCCTewN5hYe5n3ZjCA7mZk1tYas1gtyZvqNv98CBoxQVAQAMfQBUwBKDIOAYwVJe2Y5MOogOdHFlotXrFwmDlAsj/ZyvHtq04ZuLGHmOPu9HSfVZbV2IaOsziIJeFymxiwf5I7aq/tH9Fh4JdIbvxh4/8MmDDLkWk76yaGMTXMZDmY4e5 zFEL6ChViiEzyJRXu06tt6Dn/caHKe/VG sJk5nXHeHDHHPvq5R5e2iJsxMoa0dYM5AzP8AIt4qH3vKx7iS37By5WxnPmOLhdfZPGHeNcYznwX5yyG6gYvlxyBB8YxfUGfMrn WD/OAS8YjM2Rdpavme/aElOueYlZPXv5QtcMTyc HZlO7VwNT4er5mOv7eSiUzvdGIKl1lTi69T7Wb5jd/fAQdEBNi8cTcD2kXXDgbgE1me2HRlkCTg6tJsLP86zSChHsVP8BE47LhTOzxYZioIx5W0tXLGPkqpsbV34RosPp3xsZnyIReo4YivnbfW38Jzpe8aVPnka U8 yZvyxCFz6rjtSE8nhvpMLPHTTWEUIxZk7I3wuiiMnqlrlC/01bzucV68yNhHP/fo0hYtmDKGFftZmPEL3aNrhoc8p8ye78hRb9qDE8ynZV7q2fPduM1imLawaa3jp/Y8hOq7G3hi0Z5jyDLmfbft5Atde76nrb01c0tP5quDpxOfjkyndq6GJ/mzx9XMyVZ/lNPMBfNmtdOJofaT447ZWn9yPltlRr7v6XTeqN09cIwmfOkxiciGwSYEHtsvjW3Zn/9uySvEiCJkc38FrGJ8Rcxif8f2avlaeO5buzyI5oad/c/EcQ5H FYPSR0fX 7AgVN5 sNxiqXj7JK5r6jeIX4cXn1bfhV/XxHzq8T2ETivlq F5/51kRhy6Ni6HsGjZ nkYMGayMXXZ/Zcvv7h81EML3ng0EmTu/fpXNnV3l9UK4YrhosDiwOLA /FAV7o/VrjrzTcctiANy994FjEfy/ir3yvfC8OLA4sDrwuB9aBo/E3LRbBX5fgK3crd4sDiwOLA9fgwDpwrAPH4Z/DreK9RvGuPKw8LA4sDrwSB9aBYx041oFjcWBxYHFgcWBx4OEcWAeOIBn/5JZfkLn1F2LOPmkuPO/19sI/9eYXoc/m0WfR98z4PNPW1fLzzr5fLRefDc/0wMEG/Kx/dvpMW6NE8k998g9SjWRGY/wrmUdsFLfiGWHMsVvjfDU8/OY0/1QrfbtqH5zEz9/25o/pJFb/EBV/VCjHV/ Ph85nxueZto7m99Gcf4Tvj8Z8NIZL/su9yK0Dx5  cPgHxW45OLCZUFRnEvkePDMctxw4roYHH19lIZMfxJ0 1 grGodd3i5n XvkczASVy8OSfz1yBHeR IY6X5mfJ5pa Tr1tgzOH 278/AvBWvNf7lDhej2K8Dx58OHCy0t/51STeUUYBvHbsHz8wmurlmcvn8anjA9ioLGZv2rdzKHDyjT57B68GIzYc4H XLM7C o41X4Xzm5hUxJ/7VP /Q0j5w H9w8Mm3vvHwVQBScW29EfGGxCLGc2Vp88 jsqhxaYvn9EcJ502Q57d8kaj6/IyYWJRJzC7E Sx9yT7zlKPlCwGbjjIs5NhNGftbeDox7MgciTOYroCHH1uBm/j5fxnQr3E2hnttJxfoxQ42yDtzUueRGO7hxA7PvdCbduiPfAfbyPd760K/EoP1mH9gD9vWcq2LXA/gOXVlLK1nZdSNnH1lwNCJT4fzHZmOLTHpz73cyDjX/ijvIy7t5QKd5tT4oiNjrE9ykHbEQ W28s7zLmZk1/V MWgdOCAYCwKLhAsahw4JA8kgPRdyI8JazDxXljYXMUiOLXRjixZdo4PA3jNxdVt0YbfKYxf74ASPPogH7ImTvlf65Y8jsIEOip0Fa2QTDFt4tL8Xw47MkThfBQ YiRmxJ57yDH9r3vbuO7kw79hEP3mCB RW3cZQGdrkqtxgDuPkVG7kQbPKoUcbtoyl79oa X5vXaC7YtAH/Tc 2GeMNn1nc2ecA7b6iLsbHs 4mCOXna9v t6Jj/bVxT1X1mBHpmNL38GJzlu4oW zFhuZ9xHnxQOWUS6wgR5wipnWeIvhiO8zWzPM2lztOnAMF7u6MbKoQaotwngoYeFRRpLnmM9skal6KQwIrky2FFje39Kn0LZssGDia ql6MGZY BDR45lHz3EMH1n08l75ffwdGMIlpFubRyJ8xXwiAFe6YNfXba4oVxtO7lQxrnaTy4YQ NMmzySE4zVq/JHO8jVZ9o 4vs9dYH9isFDjL526wI9 OQBS1 IjQeO7BMH42ZMsh3Fh faEV/Osd RUZZ2y9YZ3Eg7W31jNct7Jxf4zrpqfCpXK4Y937MGmJfrYRdztbfu3 fg0frCAWGTFHVRgGi8vSDHRRFA2lz4fLOUzOhgXup1fo4hj2yOndlHdxZj6sb26JrFI3XQR0f9hFllvN/D04lhR ZInK Ax80p WRcj3Kjkwtk6sIKpzPvR2KIvg5O5NIGPp7puxzba7HP4Ri8XNyDi43FedyProrduc7LVr wYZ/n3KM7Ze0zXm3wrMP5jox2aLdsMX4mN9Jm9o0JbY5jnxg5xv3oyjjRz3vmVj3q81mVd3zPVhdz2lr99zlskOubDhx GkUBp2U27FykfCOqxcIBgxM7ixdzIC8LgaQ7WhjOu7UVe11A1Ac nuFHXr6xKbe3SCKjHuW32hke5s1i2JHpxvkqeM5cyDq5GMm804ED/72sa7ggb41P1gT9WhfwDFnnZWtOzzhwdDjflREjuLc23bpe3MMN7dXW NDmM3DVA8dsjerWu3ZmvoMpL/Pexayd1b7XYYN8Hz5wuAn5xjMimT9X5NkWqdADsdWD3NHC2NO/ZTfHxVm/tChTFxLHa uBY0/P1leU1DXDk7L0RzHsyHTjfBU8LGhwZfZ5ufo uiens1wgw0brfPKK/dxoujFEB3Nzk1BvbZFDb47f4vs9dTHyK/HQ79YFuvCpzufedeOsA0fauLUuUscoFzw/mxtpM/vdvHdyMcrpHif3fK/8vAVzzln99zp0tA4ckJoFgg2IPgu2m6uF4SkbGQ4RkJYx5fgqwuLi5WKUm8iRwkA3NrB3K2nZVPLAU/X4GRZc9IkBrT4pbwx8G8TH9Es9xC3jULHP8ORcbIxi2JHpxvlKeOQdMSOecow4mIdO28kFNlx00U8cuM NvBtDMDF3CyfcQS8XctZa2jri 711MfKrxtUYIksfrLTWBS1j4DZu Jl69Je42Oc598xRthOfDuc7Mh1bZ3NDP0dtJ  zXKB3lNPKyY7vHVsdzCNf19h7HDxaBw7IycWGmYcIScIiwTNkIBzkdY4LrQuh427O6qDtFIbybOjoYrFy7Ehr8czmI fCKfbRHBYiNybk6kFmpIc5Yu7g6cSwI9OJ89XwwClwE1u4Ruxo5Zdx7LSzXKAjOU1emZO6OzFUHsxbOPVJbmXr/JHvWzrvrYuRX LIdhRD6wJf0w/66M35yOqDfZ47V9lOfDqc78h0bInR9e5ebujnqB3lfcT5vVygd5RTY6/dru8zW13M2l3texw0zPP0wKHgZ2spMA4SV/Fr4bmv8Ny06kbn/VXyfAYO37LzwHqG3qXjPg6u K34LQ7sc AtDxz8jJc3Kd/IvjRJFp59knbyQwzJ59bV0XFVGQ4W8JXLHyXxZo3PV8W8cN3P6RXDFcPPxoG3PHB8tiQufz73wpSfu/kqx48H1mHjc d81fTK72fkwDpwrD xu96SFwcWBxYHFgcWBx7OgXXgWCR7OMk 40l9 bTeQG/lwMfHx6q5te6 JQfWgWMR/y2Jf tmseatg8a9HFgHjsWhezn0qvP/D/nIrL5E5hgTAAAAAElFTkSuQmCC[/IMG]

---

### Post by deadflowr on 2021-03-08
When running into ssh issues, most users run it with the ssh verbose options
like
```
ssh -vvv user@machine
```
(replace user@machine with the correct names)
This usually gives a good idea of what's what.

---

### Post by Morbius1 on 2021-03-08
Maybe I've just gotten too old for this but I'm very confused.

[1] The title of this thread is "Cannot connect to my Ubuntu server"

[2] But you aren't trying to connect to your Ubuntu server:

> When I run ipconfig in my CMD:

```
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . :----------------------
   IPv4 Address. . . . . . . . . . . : 192.168.0.254
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.0.1
```

ipconfig is a Windows command so that address is your Windows box. And you are trying to connect to the Windows box:
> ssh: connect to host 192.168.0.254 port 22: Connection refused
 
[COLOR=#ff0000]How and with what did you set up the SSH server on the Windows box?[/COLOR]

[3] You seem to have another problem with accessing the Ubuntu box:
> nicodemus@LAPTOP-TAFDGDO9:~$ alias server="ssh nicodemus@localhost"
nicodemus@LAPTOP-TAFDGDO9:~$ server
ssh: connect to host localhost port 22: Connection refused

Which may be because you have no SSH server on the Ubuntu box or a firewall is in the way. If it's the later turn it off:
```
sudo ufw disable
```

---

### Post by TheFu on 2021-03-08
My bet is the OP installed Ubuntu into a VM, but either 
[LIST]
[*]didn't install the openssh-server package or
[*]setup the VM networking (in the VM settings) for NAT, not bridged - needs to be either bridged or host-only or
[*]doesn't know the correct IP for the ubuntu system or
[*]forgot to start the virtual machine or
[*]some mix of these
[/LIST]

If the OP didn't enable a firewall, then none is enabled.

If the OP is using WSL - that changes things. It is an important detail to mention.
Of the OP wants to connect from Linux to Windows using ssh, I think Win10 has an sshd now. No clue how to set that up.
I know that Win10 ssh client will connect to Ubuntu ssh-servers.  It works the same as normal Unix ssh clients, just with Windows paths for any files specific on the command line with ssh.

One more thing:
```
_[COLOR="#00FF00"]nicodemus[/COLOR]_@LAPTOP-TAFDGDO9:~$ alias server="ssh _[COLOR="#00FF00"]nicodemus[/COLOR]_@localhost"
nicodemus@LAPTOP-TAFDGDO9:~$ server
```
I suppose you can setup an alias like this, but if the userid on the client and the server are the same, no need to specify it.
```
ssh localhost
```
is sufficient. It doesn't harm anything to include the username, but extra typing = bad in my lazy world. Might as well add the verbose switches to get more debug information back:
```
ssh -vvvv localhost
```

What is a static IP?  Websearch found this:  [https://whatismyipaddress.com/dynamic-static](https://whatismyipaddress.com/dynamic-static) I liked the images they used. ;)

I find it easiest to just force all devices on my home network to have static IPs if they aren't guest devices. Anything that runs a "server" - like ssh - is easier to access if the IP never changes.  That's a *static IP*.

---

### Post by nitchgamingstudios on 2021-03-08
I have a new problem that is most likely causing the problem:

When I run the command:
```
systemctl status ssh
```
it gives an error code looking like this:
```
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
```[/

---

### Post by TheFu on 2021-03-08
On a patched, 20.04 desktop, 
```
$ systemctl status ssh
&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: en>
     Active: active (running) since Sat 2021-02-27 12:51:13 EST; 1 weeks 2 days >
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 876 (sshd)
      Tasks: 1 (limit: 4615)
     Memory: 9.4M
     CGroup: /system.slice/ssh.service
             &#9492;&#9472;876 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
.....

```
is what you'll see.

Are you on Ubuntu?

---

### Post by nitchgamingstudios on 2021-03-08
To clarify, I am running a dual boot system and I am not using Ubuntu desktop, but I am using the Ubuntu server.

---

### Post by nitchgamingstudios on 2021-03-08
> **TheFu said:**
> On a patched, 20.04 desktop, 
```
$ systemctl status ssh
&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: en>
     Active: active (running) since Sat 2021-02-27 12:51:13 EST; 1 weeks 2 days >
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 876 (sshd)
      Tasks: 1 (limit: 4615)
     Memory: 9.4M
     CGroup: /system.slice/ssh.service
             &#9492;&#9472;876 sshd: /usr/sbin/sshd -D
[listener] 0 of 10-100 startups
.....

```
is what you'll see.

Are you on Ubuntu?

I am using the WSL and it's a dual boot system, with windows running on a separate partition from Ubuntu, but on the same drive. I am not using the desktop version but I am using the server version. Do you think I should switch over to the desktop version?

---

### Post by QIII on 2021-03-08
Maybe I have become daft in my seventh decade, but you say you are using WSL ... and Ubuntu is installed in a dual boot.  Which is it?

Or are you thinking that you can be running Windows and SSH into the Ubuntu installation on the same machine?  Or to WSL?  Or are you trying to SSH from WSL?  Are you trying to SSH to a different machine entirely?

Is it a dual boot or a virtual machine?

---

### Post by nitchgamingstudios on 2021-03-09
It's a dual boot, and I am using WSL to connect to the ubuntu server from windows

---

### Post by CelticWarrior on 2021-03-09
If you have a dual-boot then when you're running Windows you aren't running Ubuntu therefore nothing to connect to.

---

### Post by nitchgamingstudios on 2021-03-09
Ahh ok thanks

---

### Post by slickymaster on 2021-03-09
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2021-03-09
Yep, dual boot means one or the other...never both at the same time.

You can run Windows, install VirtualBox and create a virtual machine with Ubuntu Server inside of it (using Bridged network adaptor) and you can use Windows to connect to Ubuntu Server which is running in a sub-process of Windows but separately as if on another machine.

You could also install Proxmox as a hypervisor on the machine, then install Windows as a virtual machine and Ubuntu Server as a virtual machine.  Be warned that your Windows license would think it was installing onto a different machine because the machine would have different hardware (Proxmox hardware layer).  So if you have Windows license that is "retail" then you can do it with no issue but if you have "oem", it won't activate.

LHammonds

---

### Post by TheFu on 2021-03-09
There are many ways that dual boot sucks. This is one. There are others.

---

### Post by nitchgamingstudios on 2021-03-10
I have took the suggestion of using virtualbox and it works well. Only problem is that I get "ssh: connect to host ip.name port 22: Resource temporarily unavailable". How do I solve this

---

### Post by TheFu on 2021-03-10
> **nitchgamingstudios said:**
> I have took the suggestion of using virtualbox and it works well. Only problem is that I get "ssh: connect to host ip.name port 22: Resource temporarily unavailable". How do I solve this

Dude.  Troubleshooting steps provided above are the same as before.  Work through those.  If you want help, 
post the command and the output back here.  Do all the steps.  Show exact details. Do not interpret.


Please.

---

### Post by LHammonds on 2021-03-10
> **nitchgamingstudios said:**
> I have took the suggestion of using virtualbox and it works well. Only problem is that I get "ssh: connect to host ip.name port 22: Resource temporarily unavailable". How do I solve this
You will want your VM network card set to "Bridged Adaptor"

It will then get a similar DHCP IP as your machines on your LAN.  You can then switch it to static IP if desired.

LHammonds

---

### Post by kevdog on 2021-03-11
Hmm with Windows -- if you just install the Ubuntu stuff (not using a VM), I think it will install a base that will include SSH server.  If all you need is SSH capabilities, I don't think you have to use VirtualBox.  VB is OK however I find the performance just really bad.

---

