---
title: "libxm2 is outdate and won't update"
date: 2022-07-08
forum: Server Platforms
---

### Post by wseyller on 2022-07-08
I have two servers that have the same applications.  One is production and the other for development.  Both have ubuntu 20.04.4 LTS

The production server has an older version of libxml2 and is showing a vulnerability.

libxml2/now 2.9.10+dfsg-5+ubuntu16.04.1+deb.sury.org+3 amd64 [installed,local]

It acts like it has the latest update.


The dev server has a newer version

libxml2/focal,now 2.9.14+dfsg-0+ubuntu20.04.1+deb.sury.org+1 amd64 [installed,automatic]


Both of these servers in the past were upgraded from Ubuntu 16 to 18 and then to 20.


I think this may have something to do with repos difference between the two servers but not sure where to start.

---

### Post by Bashing-om on 2022-07-08
wseyller; Hey :)

Looks as if updates on the production server are in order:
> 
sysop@2004x-c:/$ apt list libxml2
Listing... Done
libxml2/focal-security,focal-updates,now 2.9.10+dfsg-5ubuntu0.20.04.3 amd64 [installed]
libxml2/focal-security,focal-updates 2.9.10+dfsg-5ubuntu0.20.04.3 i386
sysop@2004x-c:/$ 


So, what results:
```

sudo apt update
sudo apt full-upgrade

```

As to the elevated version of the dev server - where did this xx.14 version come form ?
show us:
```

apt policy libxml2

```

[INDENT]maybe, as simple as that
[/INDENT]

---

### Post by wseyller on 2022-07-11
I think the apt policy libxml2 gives me a good clue.

Looks like a ppa repo is missing from the production server.  Apparently the production server was rebuilt a year ago and the repo was never added back I guess.

Dev server
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAo4AAADJCAYAAACtzLMdAAAgAElEQVR4nO3dv47luJXAYd1CtWFjYMOwF052He3MwC9QsR/jJjac B38Dn4HJ8ZMcv0ITp0YVfkEgw03MXaBSRo22kFtUnetZpM8hzyH/6TfBxTQfXVFHpGUxEtJ1OV2u71er9dt27bt fl527Zte3p6 ujfd/fP7vbLNMtDz8/P2fSl/EviC/PKxRRLY79 7t p/MPl9zL22j6N0vxj6cfahXa5tH1etHUdW 8uLJ/7v8Pv5NIpiUGTfun F37Hu32VlrMlPql8YrFo99nU/hvmH9Oi/QLAzC77jmNvtSd4oLfWbXXFfWHFmAEANo89M7OOmAEYh/0XAHD5/e9///q73/1udBwAAACY3MOPfvSj0TEAAABgAQ8//OEPR8cAAACABTy8e/eueKXYE4appw4BAABwDJ88HFMzlUhPJdO9zLoNAAAAK3oIP9B0tkZ2yHJz5z09PX30xygoAACAn086jpLn5 dsh y PPyOdHk7XE/Kp1ardAEAAI6ueB7H3Ehe7E0kJaOT0psdNOsCAACgDdcJwHOdt9Qr3FrI3QdJBxMAAKBO1zfHpN6B7YnXoAEAALRRfI/jzOg0AgAAtNO147h/8tn7ARVtp5GHYwAAAOq4dhylp633HTumywEAAFjLR/c4htPjbNv2yVPSueVhZ9D7snFJfKkYuJQNAABQ53K73V6v1 voOAAAADC5Qz0cAwAAgHboOAIAAECFjiMAAABU6DgCAABAhY5jQ0w3ZJN7J/rRyvZo23MGJXVG/QI4CtdXDmqmw/HIw5Km9MrD1q9EtAjLtzRG6/r7dKR1W73FZ/TbgWZuHxqW8tO0H2v5aNe3bseq9QcZ9Qu05dpxvO sM40sTjs05MHivTknK2rr9fx M7Myjd/v33Z27jLWjaj7V8tOtb2tcqbRPtjk8AbFw7jjn3g0BugvDciIY0 be0vgcpfc3k5yuPWMXq0PKd2Od3NeXjUT 5tGOT3ae2Q9NJT30Wi1FaX9q/NJPne/4wyZWPZX1N 5LykNatbZ8lI7Kp5VJcqfQ92of1h6UmPu3xP5evtN/ReQTa6tZx3LbyEYr9Z9JIhNeImjZ2KX7vg9cMHc2elw/D8rN2fHJtbxbWGHPrW0dKZygra51Zb3GR2mfJiGxqHW3 petb8/eIr T4XxPbDG0UOIOuHceWB4LZDhqpX74ecdaMWrb Je7dEUuNTpTkM1ubkFjj7bW9I0bNZ vo1 xP3vGv1rEanT8AH107jjn7A7Fl1KqlGS6BWE6g0qX9lnIjiB4nFGv7SZVFyYhQ6v9HOmHO1oHz4lF/Lfcnj NjLM2RLJfBj7p/ASuYpuO4bR PKu3/ryHdL Zh9AFq9pN27vJdj8vEufYj3V/lOdo3ez3VGr1dmsvDtTzqr3XZWI6PsyvZP0e3Q Dspuo43lnvx5pZ7UF/9rJoeX9pbSyxGGYuw5mNbn8zta/RWhwf7x23sHPa21nrFFjJNBOAex oehz4cnmMOvA P smx849ZDTLJfkW379vX839aeEDOtaHLTSflazvqVX5pMreq3x7tV/tPlazjrVt1Hx/2/5VB7myb12 tfsngH4ev/vuO7fEpCdfc2I3m8fWTd3rE7vUkTtwx9LILZfi0 Sf2iYta3rW 4Is9bsn1Wvs/5o0c/Xj8VSq9j6z2u3LXa6zlo 0DaX7jxRjbbtoeRlW235r6k9z/JIux Z4HX80 dTQHr9TSvbPXKc2/DcjmIC/y9dff/36q1/9anQcQFMeHUfgTHruH yfwDoe3717NzoGoDnriAhwdCP3D/ZPYB1TPhwDtMCJCEgbvX Mzh AzjQPxwAAAGBudBwBAACgsnTHMfXUYMnULJhXrn6PVndH254zmGn6JADoxfUexzPc3DzyST9r XrVj6YMWpXT6CctV5/mw1J mvZjLR/t tbtWLX IKN gbbcOo4zTadwxIOGtXy96qdm4uNZlW7//vtnOzlp2o 1fLTrW9rXKm0T7Y5PAGy6PlWtmaA5N0GuZvLc3IiFtL4Un5RHjxGZkWJ1ZPlO7PM76wTlsTQs6Ycx37cxtR2aTnrqs1iM0vrS/qOZ/N7zh0mufCzra9qXlIe0bm37LNn/U8uluFLpe7QP6w/LHsf3XFyWtgFA7/Gf//xns8RLD0wlIxipg0PqwCGtL8UnjYS0HnGdoaPZ8/JhrH7Cf9ecOD1ibcUaY25960jpDGVlrTPLutbjh b/JfmXrm/N3yO 0uN7aWwztFHgDB7fv3/fJSPNTl2y41t/WUq/flvxyKdm1LL1L3HvjliqfkryWe1EYo231/aOGDWfraNfsz95x79ax2p0/gB8PP74xz/ultnslxCs8fXYPssJVLq03lJuBNHjhLI/kXtc5t6nW7P iB8lPczWgfPiUX8t9ydr 06lOZLlMvhR9y9gBd3ucZTu5xrNI77WB7DZT9q5y3c9LhPvRyXDPKURZs/Rvtnrqdbo7dJcHq7lUX tyybXvldXsn ObofA2TXtOLKDf6r2oD97Wba8v7M2llgMM5fhzEa3v5na12jW 1VTaYb3HI5w1joFVjJsAvDRl4U1T1ZajTj4Pj/rJsfOPeQzw0hwaQza79 3r2Y0OXxAx/qwheazkvU9tSqfVNl7lW v9qvdx2rWsbaNmu9v27/qIFf2rcu3dv8E0I/biGPsZnHpUmHJwUGzfnji2ccgra NL3WvkbT9uc 0UvHUrG 9D9ByuSxVLp7tI8xH89RnSR659Wq3L3e5zlo 0jaU7l9SjLXtouVlWG37rak/zf4vXY7NaX18rYmpJD5Jyf6Z69SG/2YEE/B3ud1ur9frdXQcQFMeHUfgTHruH yfwDq6TgAOjGIdEQGObuT wf4JrIOOI06DExGQNnr/GJ0/AJ1hD8cAAABgLXQcAQAAoHLIjuOKUzmsGDMAADgXt45jquNztg5Rj/n1zlamAABgDocccTzyTdZH3jYAADC3rk9VayZozk2Qq5muITfxqzX/HM3ksyXxl Zfmj4dUAAAUMr9zTGpt3VoJni1rr PI2TNXyK9P7Z1/kygCwAAWptqHsfSTo53p6hlJ0uTdo9OHh1JAABQa ilaonne3Bn0OPBGQAAgFZcO477y9Wpy8jW9Ldtzfv0UpeSPa1UHgAAYD1LPlX99PSUvJcReUznAwAAarl3HFOjjTElHZijdXZSD/C0zgMAAKBWt3scYyOEJZdWNevnpsSx5l8TZ oezVw82umIarePy9kAAKDW5Xa7vV6v19FxAAAAYHIP//jHP0bHAAAAgAU8vH//fnQMAAAAWMDD6 vr6BgAAACwgIcf/OAHo2MAAADAAh4 yz0TEgITWdzhHnYjza9pzBmafTAoCzmupd1RLrdDpe0/Fo5qnUzmXZIu WVnxrz56l/DTtx1o 2vWt27Fq/UFWU7 pjn1qSrBU qsfHwDIluk4pl7Zpz1AWdffr PxnRmUbv/2frfGjaj7V8tOtb2tcqbRPtjk8pJT9WpP3hbMcH4Eyq3hwjHZysy2flNdIoXYKuLZ/9 qk309SmH25X7pWP2rfilMQorX//d2798Ds18aWUlI9l/R4jjbXtU2p/mjSkuFq2j9z6XvF57J 5sm3VWZPap7X9A1iHesQxdVC6f25dLpnh12vPy4e5E1vsclDpCMCMIwLWGHPrW0dCZigra51Z1tW0z5IR2dQ62vxL17fm7xFfyQh1TWwztFEAx6fuOMY6f GJ2bK8RKzjpI2/Fe OWOr1gyX5rHYiscbba3tr2p9HnjPVZ83 5B3/ah2r0flLwvqcPV4AYxTd47g/WcROZNblGpYTaO7dz63lRhA9DtD7srV0xmPp1qzvvX2zmK0D58Wj/lruT9b2nUpzpNLR0tT/vY4fsTxHlxGA RR1HMPLzqkRxNrl2vxnlbt81 My8X5UMswzNYKZ n9t3vf8Z66nWqO3S3N5uJZH/bUum1z7Xl3J/jm6HQI4N9M9jlInsGR5Tf4zsd5/1SKWVJmj3Oj2N1P7Gs16v2oqzfCewxHOWqcA1qF qjp1QIuNqNUs96J5KvH vdTlmRmeBiyNQft97ZOboXBExHrSjuVfElPrOmpVPqmy9yrfXu1Xu4/VrGNtGzXf37Z/1UGu7FuXb 3 6ZFvjtQ vY8PAOZVNY jdECwLk9JnXBr1rfeB2i5XBZbJ3apquTkEfu dHmr9OCuvc sdvtyl us5SNtgyZ9qf1Z78NrcR/fnrb91tSf1P5S62hJ6Xu2jxqa7c8p2T9zndrw39oYSutPaiN0GoHjutxut9fr9To6jmb 59//c3QIAAAAy/q3//6v//931QTgAAAAOB86jgAAAFCh4wgAAAAVOo4AAABQqXqqenX7mzxnwfQV5zai/s/e5lpuv3fao tqdP6ezv7k9yp1uUqcRyQ9VMyI45v9/Gm5udSkOdZ6zPNmWe5ppli0Zpmn86xmmqtztNHbNzr/mB7zsz49PQ3rkJQcf2asn9G085zWzPsqnfstjlaXpxxxTJEOJuGbJXLzrvFraU618/sBJdj3ETPD8WfVtqk9p9aW72pv5xoZ3 OHDx GZLya1JsSUh3Fktcphvns04h9HrvUolmumYBZexlH2rZwuZS/Jj7LBMsalgnUveJvWT6WCfCt ZdOTp0q71z6JfGl6tKj/dVsX n GS7Xri/ln/uOJv/U pr9P/y39wsMJCX7T83y0lhS5ZOaaL3k FLT/jUxp/Ivjb 2rmPb4cWz/kuPb Fy6dhgjU/01VdfvV4ul8P /e9/fP7JX x7Ly8v2XRiy/efSculv5eXl0X5NmanlJ rV5lKYblp 03FK NeVakr81/tblE1vXs33WlKl3/ZTEF37fu/2VLvOof83 3at8a Ozxpwr8/CvdPsty0viLsnr/m PstS2H6 Yc/HH9s SGErPDa3r33qslOrGs31eLnK/iUvVO61HtCSt89Ok3zIGKe3c8hnKxjuN2CvdatOvybv0V/nMl222zfcVhiNY6l z3Mqa/sjybXELUXiFaaQRxy/v/MP0wv2z9IpQqVz6NWmnRgVjn49oP5Y86Ti KankMyu9RO2dd0uj7z2yGh2/R/4z7XPSpZ4ao7dvdP5HNrp9HGH/z2l9q4Lm9iwLzbnTmn5K6vaAWnQcsQTNPSEzp9/aDPEfvUNy9O1DvdH739nzj Xn2bH02L575007SJW6L/T /1j6Uv77dBlxhJtcoxo52ojjO3r7Gb19o/NHHvVTr/VopJdc51G7vkcM22YrI ZxfCP9egh7/GGhS8tnYPkF6NFplPIviS/13ednnzm4PGP1SsOjfKTlXuWniSH8bs/9pXf9eewflnhKyzeWlmf7s5rhaoBU3qVptXxCvLeWbXkGmvhS39HcXy4dn0vz9y5PRhzfaG6Wl 4T8L6PQIqzNAaP4W4LKf/c8tgyS8crLCMpfWv Hg9jWMrHo/xKYgvji32v58MsM9RfaR6e7aNm3dj2ttw/w/VapK/Jd/9Z7XLp4Q7v88QK VvW77H/9YwvHHmU0ktdyk6tH bvXX6Xr7766vXXv/51dQKzi706Z8ZXDrY2egSUy9w2lM/c9vVTU1fW qV9AMcldRy9Sf2my 12e71er00yn4H0zkUAAACk7TuO3OMIAAAAFTqOAAAAUKHjCAAAABU6jgAAAFA5/HQ8NU9Q555WkqYx8JzmYPSTkqknubYtv31eT4B5Pondoix5ehYAcDaMOAY0k im5qiSlh BptNylI7NUesQAIBahx9xLHHv OU6hXfhBJ7S8tpYUv9PfWcvtr52guDa2LUjsjX559b12L6SyZOl9cM0NJPvWta3tg8AADToOO7MciL1ugQqdT5T Vg6vLnRVkv UieoRfq5zq/mUnw4s78lJsvk0iUxAwCQw6Xqg1jhErJn/rG0NOn37CyV5DOibka3BwDAehhxnEyqYyNdGr9/VsJ7tNFDy/w90pbq5/7v2rRb8YgPAAA6jgfh0ZE8utx9pyX3R bS37a6J t71J8lPgAAto1L1VM58mjfLPlLT7zfn4qP0cY3 5P1s8cHAJgXHUel8ESbeoo6tVyi f49D813SzsFPTptmqmOLGlpt1l6gOf VxKfdyfMml4sfgAArLhUvSNNeSLdJzbyPrLYpdaWnZnUlDC55ZbLwZrtK0lfe8 oNsZUPLnvSWUTq7/a9bXxAQCQc7ndbq/X63V0HICJdcSU6WoAAJAx4ghsjMgBAKBBxxGH4NHJo6MIAEDew1/ 8pfRMQAAAGABDz/5yU9GxwAAAIAFPHzxxRejY0CCNGXMSlaLFwAAfOrxr3/96 gY1KwPL3g9/JB72rb1dDyjnvRNdfxmuy/Q4 nqbavbLk378notoWYez577h7Z9SPHzVhsAmNvjl19 OToGFet0KV7TrWgnsV5hKpfSGGffHitL/Wnal7V9aNevGd312D9KOrNSfivsPwBwRg8//elPR8ewDOlknZuQOfxu6nPLZej9 qk3q7S6zK19k0vuzSy59e//zq0ffqc0fW391bCmr11/1g6XFH/r8gcA Hj88OHD6BhUZjgZtowhNjoVLg//nRrNin2WG/3qxRpDbv3RI1UztE/Lts8QPwBgfo8r/qqvuQ9qtRGM1OvzSl D58l6j6g1nlU6NyPu0/PqMNe EjJct2Z9AMD8Hn/xi1 MjqGI56hKz45kbgTRa/Jqzwc79umm0pz1suhIq5dJ7Ygw7QMAzuHxZz/72egY1FY EfW4TLwflQzzTI1gpv6PcqPbZ zHCfUKAPC0zCsHOQnq5S5rU4ZtjG6f1ieiR8cPAFjDw gAvGmfGk6dKGufOpaeEi1VGoP2 7VPVnt8v/Qp4pZi9 Np6q91 0il79W ej5Vv1f6FDUdWQCY0zIjjtsWPznVTlJsvQ9QuhycSz 2LHYpueQEH/t yVPX1vQ18ecul1u3P7aeJT6v 0Rr2keKdX1t2vvPPNeX4m 5fQAAH5fb7fZ6vV5Hx4HGrB1HAACApUYcUc86ogQAAEDH8UToKAIAAIvDPRwDAACANug4AgAAQIWO4yRWeh3ijGaa6qfGjDEdyZHKt9WUSqs5axmsst2rxIlydBzf7Oc3zM11KB20Wx/UpbRHvkaxdDn6O1KdzLgtPeYffXp6Gna/8uqd1pmOj2eknUe4Zt5g6dxtQV1 jIdjdqSD8X76Gml6G6a6mRf1AtSpnV8VflY9fmnPibXta7Xp5maPL4eOo1LqTRepjmK4vCSffRqxz2OTJGuWSrTq2bijP3nVTHeq80Ps10QrXbp5nn0jKdkXYezVz9a36oWNqPx2sL90rrf/ 51A5jdXP08pVYyl z3BqbpXzD KR9P/yOVD/S prl4XdL23fJ8S1VllIZ5Vj3T6nutJ3GVj9OWtZvafql7bc0vuZut9vr5XI5/d/Ly0vx8v1n0nJN/uH3a9JMLS9JvzaP0rjD8svFZ13fIz5r/c6w/dYysWyfdnlNuZ hfMO/VuVfsy0e7aOkfsLvW9pJj/KR2rdH trjn1fMufg19VNa3l7xW5d7nD 899/ef4w47ozu0bfOT5N qxha5B17pd3KrPHPtv1Hi2fk9rS4BSa8QjKa5RWXI L3zNMjLUsa3uUXGzXUXHGyyKVfk3ZqVDD2 ertrxQdxzcljeTMai5R75eV6Fn20q0H988wFvtkO5b2nVq3Z11Z98/c prbJ 5p1G7z6ONL6/xb36qhub3KQnPus6afom1/vdBxRBdH6IjNsMMCLVj3z9H7hsfxRdqG/Y9KzfdLjD4 js4/lp9nx9KrfaRi0txPLY2Qj2x/peg44iO5RmkZbQSsaF YQeqqBO2zXuvRSC 5zqN2fY8Ytm1sGT1823QzKejfTrI/zFEFaatHwG1ktRnp1Gj1 z3r I73VY8gRg7DNNXKl1tVqPBqTS125fLo3aeKzta4Xy7SkXw4jt96wf7 OLJr WT8j31vKy6wxqj9HbppuSSjp luY/W3k /u1vfxsdwxRijSH28EVuRK7HfQiWGDyGy2vF8i69FGZ9eCm2I2rTsOav2f5c/VjLL7aeZ/pS XjUX0n Ryvfknz3n9Uulx5usO4/3vWjLV9t/ZQut2pd/h75W9ZvXX694wtHHqX0UpeyU uH Y8uv9Dlt7/97esf/vCHYQGgjxlHQAFg2zg 4dikjuNqHn/ 85 PjgEAAOCQZhsxtHp89 7d6BjQwcqNFMCxcXzC0R2pjT MDgAAAABroOMIAAAAFTqOk5jtcfvVzDTVSo0ZYzqSI5VvyZRIKLd62a4S/ypx4lN0HN/s51fKzbUkHbRbH9R7zF mNVMs0DlSncy4LT3mP3x6ehp2v9TZO63ec5PiY9p5DkvLTnNutzhbXT5 /vnno2OYhnQw3j8 Lz1ev/Kj9kdHvQB1vOefnNHqx4dV49eeM2vb32rT4cwcH68cVAorMZwAVFpeks8 jdjnsclfNcs1E4BrJ5aVti3Vsd4rjU8znUHt9mnm2bJMp6CdxytX/5ofKpb2Yz2wSuUj1f/ c6kdxurm6OUrsZS/ZrlVy/is9Rfmkcvbo35zx5ZU y85/qVikbY/x7r/Ssd2baex1Y8Xz/2j9PwXLpfObdb4zG632 vlcjn938vLS/Hy/WfSck3 4fdr0kwtL0m/No/SuMPyy8VnXd8jPmv9zrD91jKxbJ92eU25n6F8w79W5V zLT3bR8v6k7bPo35r9gWP9LXb7xVzLv4wHk0spd8f1f48zi/e 7f3HyOOO1177BGt89Ok3yqGFnmH3591WF/LGv9s23 0eEZuT4tbYMIrJL31ro/Z2mMJj9gtaXiXXWzUsHREuVQu/Zq0U6OCsc9X3L9y6Di KWkEZ1ZziXq/rETPspduPbh/hrHYJ9uxtO/Uuve60t5 0NOIdmRpv6OPP63zb30rh b2KwvNudGafopm//JExxFdHKEjRocFR2XdP0uuKKROcOxfaaOPn6Pzj Xn2bH02L5w8KEkfc39p9K2SvuXJzqO Eiu0VlGGwEr2tcxtLjsPlrsikXoSNvbW vRSC 5zqN2fY8Ytq1tGTGP4xvp10X4iyCsFGn5DKyXojw7jR6/Vr1/8d7rsOQJv9hnmrhS62q1/rWfSl 7fbk0auOxtq8VyrenXAze8dWkJ63TM36N3PHD 3wwuv20vOw6g9pj LbppqySjq l fcuT0Yc38QqO3YpJTci1 M A0sMHsPhtWJ5l14Ksz68FNvRtGlY89dsf65 rOUXW88zfal8POqvJP jlW9JvvvPapdLDy947z894pdotk9z/G2hdf145G9Zv/XxoXd84cijlJ70Y2P08TV0ud1ur9frtVkGmMOMI6AAcFQcc6HVY5TaEyOOAAAYjRwxw9pGj7iWouN4EjM3QgBYHcdYWKzUfng4BgAAACp0HAEAAKBCx3FiHlOiAAAAeHn8 9//PjoGNc/pWGrW36eTWrf1dDyjnrTKzVnlub5Ufq3LFwAApD1PBhdAwq1sfVvR53lyad7TFru5fSGK3bI60vld9q5QsAwNFwqbqANNIoTci5/27qc8tl6P36qTdnzHqZWyq/kvIFAABtPP75z38eHYPKDKNLLWMIO0albwUoHaFjxA4AAJR6/OUvf7n96U9/Gh1HkZr73FYboUq9Hq2kw fdMZzlHlMAADDG4/e 973RMRSxjJSlHsToITeC6NGBkt6hKpEeXomlae3EMuoJAMBalnpzzModjR6XifejkmGeqRHM1P8BAABCy3QcV 409pa7rE0ZAgCAWod7qlr71HCqI1r71LH0FHCp0hi03699stp6WV9av/Qpan5IAADQ3zIjjtsW73yUdB6s9xVKTzZr7zOMLYtdSi7prMW X/LUtTV9j/Wl8rPexwkAAGwuf/zjH19/85vfjI4DjXlNgA4AAM7r8fvf//7oGNCBdcQQAABgqUvVsKGjCAAALA73cAwAAADaoOMIAAAAFTqOk1jpdYgzKim/Gct6xpiO5EjlWztl2FGssu2rxAmUouP4Zj /YW6uQ mg3fqgLqU98jWKpcvR35HqZMZtaR3TfSaEUfcrlxzfZqyf0bTz6NbMsyuduyyoS zxcMyOdDDeT18jTW/DVDfzol6AOqXzy7aKYUXac0Jt a423drs8SGNjqNS6k0mqY5iuLwkn30asc9jk2Brlkvvq06tm4oz951Ux3qvND7NdEK126eZ59IynZF2Hs1c/Wt qFjaj/XEI5WPVP/7z6V2GKubo5evxFL muWlsZTWb8n nSpLy0serO1TOnZpO42tOuee9V96fA XS8dua3xo7Ha7vV4ul9P/vby8FC/ffyYt1 Qffr8mzdTykvRr8yiNOyy/XHzW9T3is9bvDNtvLRPL9mmX15T7Gco3/GtV/jXbUhvL/d8eZand/71izsUfxqOJpfT7Pevfuk9KddP6 Muf7x8jjjujf9G0zk TfqsYWuQde2Xhyqzxz7b9R4tn5Pa0uAUmvEIykkf ljS8tz82aqi54mKRS78m7dSoYOp1sL2NbrNnRsfxTclOcmY1l6j3y0r0LHvp1oP7ZxiLfbIdj/ZtqZ/R 1fr/FvfqqC5vchCc y3pp iuX0F/dBxRBdH6IhxwMJRjd4/z55/LD/PjqXH9uXu29fcTyzd4yht6/5Hveb7aIeOIz6S2ykto42AFe1rbtRPvdajkV5ynUft h4xbNu8ZXQGzOP4Rvr1Ff5iSj1FnVo A8svaO9Oo9dlMU/3Oix5AjL2mSau1LparUdDUulrty XRm081va1Qvn2lIuhNL7WT4j31vKy6wxqj1HbppuSSTp lOY/e3meDSOOb2I7Q zhi9yIXI/7MCwxeFwuqBXLu RgoKkfSexApE3Dmr9m 3P1Yy2/2Hqe6Uvl41F/JfkfrXxL8t1/Vrtcetlj9 UAAADFSURBVLjD zi3Qv6W9Vu3/97xhSOPUnqpS9mp9cP8R5cfPna53W6v1 t1dBxobMYRUADA8UkdR6yFEUcAANAMI4bHQsfxJNhJAQCjcA46Dh6OAQAAgAodRwAAAKg8fPfdd6NjOK3clAUj859VbBqH1bYBAICVPXzzzTejY/iINMdTyTxylvzpkNTRlF1N2d6fwLPMIQYAAGwe379/PzqGj0gdA /5z/bC6QFGTRew6k3E /JKlZ1H3aXmyms5zxsAANi2/wPUtQqtgr4RkwAAAABJRU5ErkJggg==[/IMG]

```


libxml2:
  Installed: 2.9.14+dfsg-0+ubuntu20.04.1+deb.sury.org+1
  Candidate: 2.9.14+dfsg-0+ubuntu20.04.1+deb.sury.org+1
  Version table:
 *** 2.9.14+dfsg-0+ubuntu20.04.1+deb.sury.org+1 500
        500 http://ppa.launchpad.net/ondrej/php/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
     2.9.10+dfsg-5ubuntu0.20.04.3 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu focal-security/main amd64 Packages
     2.9.10+dfsg-5 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages



```

Prod server
```


libxml2:
  Installed: 2.9.10+dfsg-5+ubuntu16.04.1+deb.sury.org+3
  Candidate: 2.9.10+dfsg-5+ubuntu16.04.1+deb.sury.org+3
  Version table:
 *** 2.9.10+dfsg-5+ubuntu16.04.1+deb.sury.org+3 100
        100 /var/lib/dpkg/status
     2.9.10+dfsg-5ubuntu0.20.04.3 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     2.9.10+dfsg-5 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages



```
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAowAAADKCAYAAAAvrRGOAAAfIUlEQVR4nO3da5LkKK AYfvEt6Xa/wKq9lTnT eMmwEkIXH1 0RUzHQ6uRiwU4lt8r7v /ea4Pv7 /r6 ppRNGDSe6zueCzsWGcAQLv/jSro /v7r3/zYQPsg MXAN7tnjXDCAAAgD383 wKAAAAYG0EjAAAAKgyB4zpvUyl1wAAAHCGvx56 QR q97QXqsfN UDAAD08dcMoybImhmIlcr LPHx/GPWEwAAIIbpkvT393c1EPtsT98jXcZO00nltOqVLwAAwMlM6zDWZu7ShXytC/t 3vtMp82Dy88AAAD9hC3cXQvaPoGmNRBsUbvPkcASAADAbtgvvTxnJ3sGiwSFAAAAsY5Zh5FgEQAAoI9hAePzSeboB0 0wSIPvQAAANiFBYzS09PPgI5lbwAAAPbxzz2M6TI313X956nn2vY0CIy PGypX6kOXLIGAACwu /7/p1dCQAAAKzrmIdeAAAA0AcBIwAAAKoIGAEAAFBFwAgAAIAqAsZOWDbIp/ab5ae17Wn78waWPqN/AZwg7KcBNcvaRJThyVP6acLeP13okbavtY7e9M98pLS9fnVn9q/5rDw NDztpxk/3vbRpvfux679Bxn9C/QTFjB DtKVD1hpwfBVFxTPtamlnb3pn2ki3rMC6/4/37/yGO9BM3687aNN7xlfu4xN9Ds/AWgXFjDWfA7 2sLetRkMadFuKX0EKX/NouU7z1Dl tDzntzrHy3tE9E/tbxzi9SX9kMTnJdey9VRSi8dX5pF7yO/kNTax5NeM76kMqS0rePTMgNb2i7Vq5R/xPjwfqHU1E97/q VKx13BI1AP0MCxuuyz0g8X5NmHqJm0LR1l offdJaIcAceZkwbT9vwFMbe6vw1rGW3jszukJbefvMeyuLND4tM7ClNNryrem95UfUz3L b6nbCmMUON2wgLHnCWC1k0Xpm25EPVtmKXt/844OwEqzEZZyVhsTEm99R 3vjFny1QL8luMpuv67BVSzywfgNyxgrHmegD2zVD2tcKnD88EpXcLvqTZjGPFB4h0/pbawzACV/n3SB VqgVuUiP7reTxFnB9zec7kudx96vEFrG6JgPG6/p5Fev5bQ7ofLMLsE9PqH9a1y3QjLgfXxo90/1Tk7N7q/dRq9n5pLgO3iui/3m3jOT uznJ8zh6HwJstEzB eO 3WlnryX71tuh5/2hrXXJ1WLkNVzZ7/K00vmbrcX78BGxpUDraW/sU2MUSC3dHn6BGnPBqZcw64X5/6xa1rj08tMql9x7v/ xfy/1n6YM33ocoNK9Z0kfq1T6lto9q31HjV3uMtaTxjo2W91/Xv31Qa/ve7dt6fAIYo8vC3daZtNxN5Lm0pXt5cpc0aifsXB617VL9NOWX9knLm5/3vh9P/z5J/Zr7tybPWv9EPGWqvY sdf9ql W87SPtg/X4kerYOi56Xm7Vjt W/tOcv6TLrjVR5x9NOS205 8Sy/FZC2bT/2fGEoh13/f9O7sSQE8RASPwJiOPD45PYA8EjHgFzwwIcLrZx8fs8gHICBgBAABQtcRDLwAAAFgXASMAAACqtg0YS08BWpZYwbpq/Xta3522P2 w0jJIADBCl2V1ruvMm5ZnPrnnbd o/tG0Qa92mv3k5O7LdXjaTzN vO2jTe/dj137DzL6F gnJGBcaVmEE08W3vaN6p WBYtXZd3/5/vf9qGkGT/e9tGm94yvXcYm p2fALQb9tOAmoWVawvbaha9rc1QSOml klljJiBmSnXR5735F7/8C4snsvDk39a588 lvZDE5yXXsvVUUovHT aResjv5DU2seTXjO pDKktK3j03L8l7ZL9SrlHzE vF8oR5zfa/XyjA0AOt0CRusJyTJjUToplE4YUnqpftLMR 8Z1hUCzJGXCXP9k/5/ywdmRF178daxlt47M7pCW3n7zJPWe/7Q/NtSvjW9t/yI lnP79a6rTBGgdMNmWHUHMyWA977TVL6tttLRDkts5S9v3lHB2Cl/rGUs9sHiLe o/Z3xiz5agF y/EUXf/dAqrZ5QPwm3ZJejXe o3YP88Hp3QJvafajGHEB8nzAzzicvYz35b0M76MjLBa4BYlov96Hk/e8V3KcybP5e5Tjy9gdUMCRul rdki6tf7xLX6h3XtMt2Iy8HPWci0TGlGOXJ2b/V ajV7vzSXgVtF9F/vtqmN791Zjs/Z4xB4s24BIwf2f7We7Fdvy573b7bWJVeHldtwZbPH30rjazbv/ailPNN7Cmd4a58Cu5iycPfsy7 aJyW9Zpx0v791i1rXHt5ZYebXWgft z/71zJ7nD54432IQvOaJX2kXu1Tavuo9h01frXHWEsa79hoef91/dsHtbbv3b6txyeAMUJmGHM3gUuXBC0nBU369APnWQcpvbZ pXuJpP2vvaZVqk9Leu99fp7LYqV2iRwfaTmapzgtZdTSte5f7bKct32kfbAeX1IdW8dFz8ut2vHb0n a41 67FrT /zaUidL/SSW47MWzKb/z4wlEOu 7/t3diWAniICRuBNRh4fHJ/AHggY8QqeGRDgdLOPj9nlA5ARMAIAAKBqykMvAAAA2AcBIwAAAKqOCxh3XJJhxzoDAID3CAkYSwHP2wKhEevjva1NAQDAfMfNMJ78dN3J wYAANY15Lekr6u bMJnza3awraaZRdqC7Z6y6/RLBprqb 1fGv BJ4AAMDkvu/fiL fn5/iv9Ntue2e9NLr3vJb26BH S37VyuHP/74448//vjjT/obNsMosc56Rc S9Zx10 Q9YtaPmUUAANBi2iVpSeTv1K5gxAMxAAAAPYQFjJ g7vnfdLs3/ va8z680m lRtqpPQAAwF62e0r66 vrPw oQIdleQAAQIvQgLE0u5hjCVxOC3Jy xO9j6e1GQAAmGfIPYy5GUHLJVRN trSNt7yW pZugezVh/tskKt 8dlawAA0OK 7/t3diUAAACwru3uYQQAAMBYBIwAAACoImAEAABAFQEjAAAAqggYF1VaFufEtRRP2583ePOyWADwRsv8lrTEuyxO1LI6mnUmtWtR9ii7px1/ZefJ036a8eNtH216737s2n QtfRvKaAvLe1Vyn/38wOAui0CxtJP62lPTN70zzQR71mBdf f739b0KEZP9720ab3jK9dxib6nZ9KLF9SpOPhbecH4C3Ml6Slk5J3 6qiZhalS82t7fNMX/olmdb80/2q/TSj9ldsLHWU0n/ v5Y fU9L/Uos7eNJP2JmsXV8SuNPk4dUr57jo5Y qn4Rx2etbXsFadL49I5/AHtQzTCWTkaf173bJSt8Wx15mbD2gZa77GP9xr/iDIC3jrX03pmPFdrK22eetJrxaZmBLaXRlm9N7y0/on6WGemWuq0wRgGcTRUw5oK 9APZs90iFzBp699LdABW plASzm7fYB46ztqf1vGX0SZK/Vny/EUXf/dAqrZ5UvS/ly9vgDGU9/D PyQyH2AebdreD44a7/N3FttxjDixPxsW08Qnsu3JX30/q1itcAtSkT/9TyevOO7lOdM1tnR0r jzh 5Mme3EYC1qAPG9PJyacawdbu2/FXVLtONuBz8nIVMyyzNWJb 3Vr2p/yV 6nV7P3SXAZuFdF/vdumNr53Zzk Z49DAO/VfA jFPxZtreUvxLv/VU96lJqc9jNHn8rja/ZvPejlvJM7ymc4a19CmAPqqekSyey3Axay/YomqcMP 8rXYZZ4ek ax2079c iZlKZ0C8H9a58i116t1Hvdqn1PZR7Ttq/GqPsZY03rHR8v7r rcPam3fu31bj8 Icmuk8Rl9fgCwJvM6jNKJwLu9pPRB25Lee5 f57JYLk3ukpTlQyP3fukylvWkrr2PrHX/apflvO0j7YMmf2n8ee z63Gf3pN2/Lb0nzT Smm0pPwjx0cLzf7XWI7PWjCb/r 2Dtb k8YIwSJwpvu 79/ZlUBfEQEj8CYjjw OTwA7IGB8Cc8MCHC62cfH7PIBQELACAAAgCrzTwMCAADgXQgYAQAAUEXAuIAVlvLBPDP6/ 1jrvfyOCvnt1v5kVZZOm2WXfZ9l3q DQHj9ff6Z7W10KSTzYh12jzbI61UF623f1jMttJam7PN3r/Z5eeMWF/16 tr2gNFlvPPiv0zm3ad0pZ1W6XPfo T tK8DuOppJPIc5kLaRkMlsRYU v6fIAFxz5yVjj/7Do2tZ pre2727JWs pHwKhQ mWDUoBo dnDtJxnHrnXc4vjarZrFk7WLrwr7Vu6XSpfU7/ey454Fj6Pqn/P9mldNDuifOui0qX2ruVvqV pLyPGX8v WY/PdLs2vVR 7T2a8kvpNcd/ v/RPzwgsRw/LdutdSm1T2mBdMv5pWX8a pcKt9a/9a zu1HlMj t57f0u3SucFbv6r7vn/f/vfz82Pe/nxN2q4pP31/S56l7Zb8W8uw5pu2n7Td074t7Wop31v/3u2TSxs5PlvaNLp/LPVL3x89/qzbIvpfc3yPat/W nnrXGvz9M 6/57tlnpbyvr8f0RbasdPVJ1r9c8dn5Y6WD8beve/91wp9U3k JT mGH8o/cMlqR3eZr8e9ZByru2fYW2ic4j99Nrrfm3lG39Fr7y5Znriv2pwRk8/a/Z7uXNf2b79rhVKL2iNNOM81d0 Wl 6fFpvQJkVcu/Je/SLGDu9Rnjp7VMAsbL1rlvZr0UHV12T7PvLfKaXf I8lc65qRLOi1m79/s8k82e3yccPzX9L4lQXMblofms9Obf0npNoAWBIxYnuaej5Xz722F p8eiJy f2g3 /h7e/m58iIDyoj9 wRt2smp0n2fn3/n8pfKf bLDCPcaoNp5uwiznf6 Jm9f7PLRx3906737GOUWtCoTR9Rh tqbyPWYbzkbwtphJ82trR9BZ5vfBHBolS pX6l935/x6yhFVnXqDwi2kfaHtV mjqk7x15vIzuv4jjw1Mfa/vm8oocf14rzP5L7W3Nq cT36P1HMsr0NSv9B7N/ePS dlafmR7MsN46W6Cl 4DiLxPQFNPax0iprU9pPJr23PbPAFX2kZS/t7yIx6y8LRPRPtZ6pbWL/e kQ prNB/1jIix0dL2tz 9jw 03Q98teU 3ytdbv00Eb058QO5XvSjzj RtYvnWmU8itdsi6lT8uPbL/7vu/fppTYxuwZTy5n 9A a3v2T0tfefuX8QGcSwoYR2KGEQAcRlxdAPBOs2dYn5hhBAAAQBUPvQAAAKCKgBEAAABVBIwI5V2Sw1MOAADog4AxIa2v5dkeVY8RSoHfqHpFlrNKwHr6 mQAgHMRMD5oFr8trTElbT B5smsU54SPbUPAQBowbI6f3wCvlow JEuvCltb61L6d l9zzl0msX9m2tu7S0iKf8WtqI/bMseiylT/PQLJrrSe8dHwAASAgY/1jlAzRq4V8p6CyV4wl0a7OrnvKl4KdH/rWgV7OIaroSv6dOnkWhLXUGAKCES9IH2OFScWT5ubw0 Y8Mkqw/zTba7PEAANgLM4wLKQU00iXwz2sW0bOLEXqWH5G31D f/2/Nuxd iQQA4EXAeICIAPJ0tftKLfc/1vK/Lvk zpwR/eepHwAAXJJexMmze6uULz3B/nnKPUdbv9WflF 9fgCANREwKqQfsKWnokvbJZr3f8rQvNcaDIwI1jRLFnny0u6z9GBObq1JqX7RwVf0eo0EhwAALy5J/yEtXSLdBzbzPrHcJdWeQUxpaZfads9lX83 WfLX3hOqrWOpPrX3SW2T67/W9Nr6AQBQct/3/Tu7EoCHd4aUZWcAAKhjhhGvxwwcAAB1zDACAACgiodeAAAAUEXACAAAgCoCxkVJS7/sZLf6AgCAv23z0Iv3oYSohxpqT8/2XlZn1pO7pYBvtQdDIp6Wvq62/dKMr6ifD9Sswzny NCOD6n /AoNAKxri4DRu xJ1LIp2sWnd1iSxVrH1ffHy9N/mvHlHR/a9C2zuRHHhyWIlcrb4fgBgLfhkrSS9CFdW0g5fW/pdc/l5mf60i h9Lqcrf3lldovqdTSf/6/lj59jzV/bf 18OavTb9qoCXVv3f7AwD8tphhXOFDsGcdcrNR6fb0/0uzV7nXarNdo3jrUEs/e2ZqhfHp2fcV6g8AWNsWAeNTy31Ou81YlH7mzvpzdZG894B667NLUDPjPryoQLn1pxvTtC3pAQBr2ypgjJxFGRlA1mYMIz5Yvb9jLT20UHqAg6Dgb7u3SesMMOMDAM63TcC48wfQiMvBz1nItMzSjGXp37CbPT5zX0roVwBAlC0CRj789GqXr2nDPmaPT 8TzrPrDwBY31FPSWufAi59QLY RSw99WllrYP2/a1PSke83/pUcE 500/dd7fJTyjxpfI5 Sf7I FU0ACwDr2WKG8bryH0qtiwt77/OTLvvW8s9ty10ytnyw595veYram7 m/rXL4t79z6Xz1C/qPtCW8VHiTa/N /laZHqp/j33DwDgd9/3/Tu7EujLGzACAIB3I2B8CZY9AQAArQgYAQAAUHXUQy8AAACIR8AIAACAKgLGBez0s4UrWmnJnhYr1ukkJ7Vvr6WRdvPWNthlv3epJ2wIGK /1yesrVUonax7n8ylvGf 3KF1O8Y7qU9W3JcR64d fX1Ne2Bt92B1pfPjG2nXAW5Z91f67PagL/ 1zTqMvUkn4ecyNNIyNSxZsy76BWjTuj4q4ux6/tJ JraOr92WjVu9fiUEjAqlX6YoBYjpdks5zzxyr cWN9Zsl35PupS2VM/ae0oB9ZO1fpplgVr3T7NOpWdZIu06mLX 13xB8YyfiJ8XfLL2//N1aRzm ub09pV42l z3Vs3T/um9ZOO/fQ9Uv9I6TXb0/dax7fl/FZqS6mNarzHp9R32mCx15eSnv1rzd86fq316 q 79 3//38/Ji3P1 TtmvKT9/fkmdpuyX/1jKs9U7br1Y/b/qI nn7d4X997aJZ/ 021va/Q3tm/71av WfYkYH5b Sd/vGScj2kca3xH5a89/UXWu1V/TP9b2jqq/d3vE50f08TvyjxnGP2ZH8L3L0 Tfqw49ys799NzOvPVfbf9Pq8/M/elxq0t6RWQ2z09Rzqh/ZJkReXnyiG6/3Cyh5gqTRy3/lrxLs4C513cffxYEjJdtcLxZy6Xo5zaLkW0v3WLweQ1zcUz24xnfpbQj 8p7fNbSa26T OTRus zzy 9y 99S4bmNioPzWefN/8S7fgbgYAR3Z0QgM0 UIFevMfn7GMj4vwi7cPzy6Tm/Razz4 zy8 VFxlQRo2PUp0090tLM Izx58FASP URuMntlFwIvxhRWUrkIwPtv1nn2MUgsatekj6nBd89qIdRgv dtG g0h7Sxp wq8l5wig8WIb6/R34A/fWh5oi/3mqZepbRavb/9l/LX7l8tj9b6eMfXDu07Uq0OM/Y/sn izy a8no 8T5az8urK2g9R1 Xbmkp6fxpLX l9mSG8coPgtxDFbUZuBH3GXjqEDEt3ipXtvWSl/ehpNwBqM3DW75m/2v9422/XLrI/KX2ieg/S/mnta l3Odrrdulhxa8x090/2jbV9s/1u1evds/onxP t7tN7p 6UyjlF/pknUpfVr 7PZ7uu/7/p1SMoZZccYTAK6L8xPOJgWMO2GGEQAAoIOVZgi9mGEEAABAFQ 9AAAAoIqAEQAAAFUEjAtY6bH5Ha20ZEqLFet0kpPa17K0Eex2b9td6r9LPfE3Asbr7/WRamslSSfr3ifzEeuPaa1UF ic1Ccr7suI9Qu/vr6m3TD/9mA1em1R/E27TqG17TSf7R5v6kuekv5DOgk/H4OXHpPf9ZH5N6BfgDbR60euaPfzw671135mto6/3Za1WbV BIwKaeelC3dK2y3lPPPIvZ5btFWzXbNwt3ZBWGnfSgH1k7V mmUJWvdPs06WZ1kE7Tpctf7XfEHxjB/vCVVqH6n/n69L4zDXN6e3r8TT/prtXj3r5 2/tIxa2RH9Wzu3lMa/5fxXqou0/zXe41c6t2uDxV5fWiKPD vnX7pd mzz1s/lvu/ft//9/PyYtz9fk7Zryk/f35Jnabsl/9YyrPVO269WP2/6iPp5 3eF/fe2iWf/tNtb2v0N7Zv 9Wr/ln0ZOT569p 0fxH923IsROSv3f oOtfqn9ZHUxfr 2eNv4jPl jjO/KPGcY/hkXoBb3L0 Tfqw49yk7fv L0vYW3/qvt/2n1mbk/PW51Sa IjDa6P1YbjxYRdffkEd12uVlC6wyyVS3/lrxLs4C513c8vkoIGC9b579Zy6Xo5zaLkW0v3WLweQ1zcUz24xnfpbSfvtLeZjDSjHHkGb zzz 9y 99y4bmNisPzWejN/8SzfEVhYAR3Z0QgBGo4FTe49NyBaH0wcbxVTb7/Dm7/Fx5kQFlxP6lkw6W/DX3l0r7Kh1fUQgY8Y/aYPPMLgJejK8z9Li8PlvuCkXqpP0drffsY5Ra0KhNH1GH6 rXRqzDeMnfJtJvAGlnSNtX4L3kFBksRnw7jf6GlDyxN7udc09Sql1er97b6Uv3b/anm01sc7vnZo35FqdYiuX0t UpqR9deonT iPw9mj5 el1dX0HoOvy7d0lPS dVa/sj2ZIbxyndy7pJJbQZuxH0EnjpETHu3ypVtveTlfSgpd4Bp8/CWr9n/Wv942y XLjJ/qX0i s9S/mntayn3 VrrdumhhOjjZ0T9JZr905x/e jdPxHle9L3Pj Mrl860yjlJ33JmH1 fbrv /7tkjOWseKMJwCcinMutEbMSkdhhhEAAIeZM2TY2 wZVgtmGAEAAFDFQy8AAACoImAEAABAFQHjoiKWNgEAAIiwzUMvkcuqtKR/5lNK23tZnVlPTtXWnIpML7Vf7/YFAAB5WwSM3sfOox5blxaL7b3KeiRrHb37I6WX2m 39gUA4CRcklaSZhalhTSf7y297rnc/Exf qWLVS9nS 1naV8AABBvixnGFWaTetYhDYisq/hbZ SYoQMAABZbBIxPLfex7TYjVfoZM0ugFx0QrnIPKQAAGG rgNEzM1Z6wGKE2oxhROAk/capRHooJZenN3hllhMAgH1sEzDuHGCMuBz8nIVMyyzNWJb DQAA8LRFwLhzsDha7fI1bQgAAFoc9ZS09ingUgDa hSx9FSvlbUO2ve3PintvXwvpbc Fc0XCAAAxrrv /6dXQlJxMLPmvsGtelbypek9bOuHVl7qCRiHcoRD72wcDcAAGvaImCET9TC5QAA4J0IGF CZW0AAEArAkYAAABUHfXQCwAAAOIRMAIAAKCKgHEBO/1s4Yos7bdiW69Yp5Oc1L6tS3 dYpd936WegAUB4/X3 oS1tQqlk3Xvk7mU98yfO7Rux3gn9cmK 9K7Tp VDWY9sGY5v63YP7Np18FtWSdX uzyoC/xscUvvYwgnYSfy9BIy9SwZM266BegTbqA/qw67Ej7mdDavrstm7Z6/ZBHwKhQ uWRUoBYWnhbU84zj9zrucWrNdul35MupS3Vs/aeUkD9ZK2fZeFvabvm5Jq 5lmWSLsOZq3/NV9QPOOn98LuUv8/X9cs4N5S/53bV Jpf812a12s/etZ2F97fpPqXCrfWv/Wvs7tR5TI/ree39Ptmh/G6Dk 4XDf9 /b/35 fszbn69J2zXlp 9vybO03ZJ/axnWeqftV6ufN31E/bz9u8L e9vEs3/a7S3t/ob2Tf96tX/LvrTW5fP/EW2pPf6j6lyrf1ofTV2s7x/Z/95jUuqb3udf/uL mGH8Y/Y3mN7lafLvVYceZafv3/0bp7f q 3/afWZuT89bnVJr4jMFFG J4/o/c/NEmqusHjU8m/JuzQLmHt9xviZPWbfioDxsh0cb9ZyKfq5zWJk20u3GHxew1wck/1EjG9P/8w vnqX3/uWBM1tRB6ac783/xLNbSoYg4AR3Z0QgHGiwqlmH59vLz9XXmRAGbF/tfvyNfcLS/cwSvv6/DKveT/6IGDEP2oHo2d2EfBifK2N/mnXe/YxSi1o1KaPqMN1rdtGp2Mdxkv tpV Qyo9FV3avgLPN boYDHq8lekTx9anmjMvaapVymtVu/Zj1L 2v2r5dFaH /42qF9R6rVwVq/3k98j9bz8uoKWs9R16VbWkk6f1jLX70934QZxit/EOQeqqjNwI24z8JTh4jLAq1yZVtOApr keROQNo8vOVr9r/WP972y6WLzF9qn4j s5R/Wvtayn2 1rpdemgj jy3Q/me9L3H/ j6pTONUn6lS9al9Gn5s9sP/7rv /6dXQn0teKMJwDgfFLAiH0wwwgAALpghvAczDACAACgiodeAAAAUEXACAAAgCoCxklqSw/MLH9VueUYdtsHAAB2tVTAKK3RZFkHzlM gUgbTdu1tO3niTrPGmAAAKDdUk9JSwFB9PplT lj/rMe 9/16bFne5XaLqLvSmvd9VynDQCAt/vfddU/4NPfcPyQfptSCr56/zpArvzSwr1SsFNalLQUsKTbcnnU9kETbHkWrrbmL/Vfuj1d2PX5Hs0vTOQWHa/9u1QX1voCACDGf2YYtcGdJsga9WGtKV8zg1gLamoBibV9SkFTqWxv 0rlj g/ZmsBANjX/wNfIzEXGas KgAAAABJRU5ErkJggg==[/IMG]

I am thinking that I can just add the repo by executing

```
[COLOR=#333333]sudo add-apt-repository ppa:ondrej/php[/COLOR]
```[COLOR=#333333]
[/COLOR]```
[COLOR=#333333]sudo apt update[/COLOR]
```

---

### Post by coffeecat on 2022-07-11
Support, not chat.

*Thread moved to **Server Platforms**.*

---

### Post by #&amp;thj^% on 2022-07-11
Don't know for sure which you will get, I'm on 22.04 and shows:
```
 apt policy libxml2
libxml2:
  Installed: 2.9.14+dfsg-0+ubuntu22.04.1+deb.sury.org+1
  Candidate: 2.9.14+dfsg-0+ubuntu22.04.1+deb.sury.org+1
  Version table:
 *** 2.9.14+dfsg-0+ubuntu22.04.1+deb.sury.org+1 500
        500 https://ppa.launchpadcontent.net/ondrej/php/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     2.9.13+dfsg-1ubuntu0.1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
     2.9.13+dfsg-1build1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```
But yours looks like the PPA was added already.
Are you saying this " _*** 2.9.10+dfsg-5+ubuntu16.04.1+deb.sury.org+3 100_" won't update then?
Even on Focal the version should be>>>" libxml2 	2.9.14+dfsg-0+ubuntu20.04.1+deb.sury.org+1 "
Source: [https://launchpad.net/~ondrej/+archive/ubuntu/php?field.series_filter=focal](https://launchpad.net/~ondrej/+archive/ubuntu/php?field.series_filter=focal)
EDIT: I always *dread* suggesting using this option, but sometimes necessity makes it a reality:
```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install libxml2 2.9.14
```
I find it works for me 98% of time, BUT STRONG WARNING>>> your mileage may vary so **use at your own risk here on a production server.**

---

### Post by wseyller on 2022-07-11
The ppa repo was on the dev server but is not on the prod server.

It will not update and it says that there is no update available.  Acts like it is on the latest version.

I have a meeting tomorrow to which I will bring this up and will suggest changes.  I want to add the ppa repo and try again.  The command you mentioned might be a good one to try if I run out of ideas.  So what will likely happen is I try to fix it sometime this week depending on when the change control gets approved.  I always snapshot the server before I do this, and revert back if it blows up.

---

### Post by #&amp;thj^% on 2022-07-12
> **wseyller said:**
>  I always snapshot the server before I do this, and revert back if it blows up.

Should be good to go then..:)
Some of the problems that are associated with the force command is it breaks some dependencies needed. ( the risk of introducing breaking changes)
Like i said it's a crap-shot, but works for me more often than not.

---

