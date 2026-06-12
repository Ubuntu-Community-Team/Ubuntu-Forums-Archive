---
title: "Trouble with DVD"
date: 2005-10-28
forum: The Cafe
---

### Post by Joh_ on 2005-10-28
I seem to have trouble with DVD's, authoring or watching. Not sure myself. And I thought, since I know absolutely no one using Linux, or even dvdauthor and well, someone here's bound to be technically knowledgeable. ;)

I'm trying to make a DVD with 20 titles using 2 menus. Altogether these titles/menus are 3.8 GB which fits a normal one-layer DVD. Now to the problem...

Authoring gives no problem at all, and the DVD works perfectly, with menu and everything while watching it on a computer. Even after burning it, it works flawlessly on a computer. The problem is, it won't work like it's supposed to on either of my 2 stand-alone DVD-players...

One is an Eltax 
DV-100, the other is a Mustek DVD-V-56L-2C. On the DV-100 the first menu works just fine, and jumping to any of the titles listed on it works just fine too, and shows without no problem. This is also the case on the Mustek. The second menu on the other hand isn't working as flawlessly... The first 4 titles (title 11-14) works just fine on both of them, all other titles causes the DVD to stop, except for the DV-100 that spins and spins and never gives up until you turn off the power.

I've tried burning it to a DVD-RW, which resulted in the way I just described. I've tried a DVD-R, same there. I've tried a DVD-R on another burner, computer, OS and even writing speed. No success. I've also tried a DVD+R. On the Mustek this gave the same result. When trying to play title 15-20 it just stops spinning just as if you pressed stop on the remote. On the DV-100 however, all titles up 'til 17 work with the DVD+R so now it's only title 18-20 that causes the disc to spin endlessly...

Now I want to know, what exactly might be causing it? Bad authoring? Bad media (even though I've tried 2 brands)? Bad burning (using K3b, except for one of the DVD-R's, that was burnt in Nero)? Anything else?

Thanks in advance for any reply that might help. This is my dvdauthor.xml file:
```
<dvdauthor dest="/home/johan/dvd-root" >
 <vmgm />
 <titleset>
  <menus>
   <video format="pal" resolution="720x576" aspect="4:3" widescreen="nopanscan" />
   <pgc entry="root">
    <pre> if (g3==2) jump menu 2; </pre>
    <button>jump title 1 chapter 1; </button>
    <button>jump title 2 chapter 1; </button>
    <button>jump title 3 chapter 1; </button>
    <button>jump title 4 chapter 1; </button>
    <button>jump title 5 chapter 1; </button>
    <button>jump title 6 chapter 1; </button>
    <button>jump title 7 chapter 1; </button>
    <button>jump title 8 chapter 1; </button>
    <button>jump title 9 chapter 1; </button>
    <button>jump title 10 chapter 1; </button>
    <button>jump menu 2; </button>
    <vob file="/media/storage/Temp/Bleach-01/menu1.mpg" pause="inf" />
   </pgc>
   <pgc>
    <button>jump title 11 chapter 1; </button>
    <button>jump title 12 chapter 1; </button>
    <button>jump title 13 chapter 1; </button>
    <button>jump title 14 chapter 1; </button>
    <button>jump title 15 chapter 1; </button>
    <button>jump title 16 chapter 1; </button>
    <button>jump title 17 chapter 1; </button>
    <button>jump title 18 chapter 1; </button>
    <button>jump title 19 chapter 1; </button>
    <button>jump title 20 chapter 1; </button>
    <button>jump menu 1; </button>
    <vob file="/media/storage/Temp/Bleach-01/menu2.mpg" pause="inf" />
   </pgc>
  </menus>
  <titles>
   <video format="pal" resolution="720x576" aspect="4:3" widescreen="nopanscan" />
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-1.mpg" chapters="00:00:00.000,00:01:35.880,00:02:33.400,00:04:15.359,00:06:31.399,00:08:37.919,00:13:26.159,00:16:23.040,00:18:48.279,00:19:39.200,00:20:51.479,00:21:49.000" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-2.mpg" chapters="00:00:00.000,00:01:26.399,00:02:35.520,00:04:29.760,00:06:23.040,00:09:46.080,00:11:18.720,00:13:36.479,00:15:06.239,00:15:33.599,00:17:55.200,00:19:39.360,00:20:41.759,00:21:39.360" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-3.mpg" chapters="00:00:00.000,00:01:36.000,00:02:19.680,00:03:10.079,00:04:27.840,00:07:07.679,00:08:17.760,00:09:32.159,00:11:11.039,00:13:38.880,00:16:08.159,00:19:09.119,00:20:51.840,00:21:49.200" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-4.mpg" chapters="00:00:00.000,00:01:36.000,00:02:18.719,00:03:36.479,00:07:43.680,00:08:57.599,00:10:16.799,00:11:34.560,00:13:15.840,00:15:12.000,00:17:07.679,00:18:36.000,00:20:51.840,00:21:49.439" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-5.mpg" chapters="00:00:00.000,00:01:36.000,00:03:24.719,00:05:39.000,00:07:00.479,00:09:29.280,00:11:27.840,00:13:09.119,00:14:05.760,00:16:34.080,00:18:34.080,00:20:50.400,00:21:49.080" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-6.mpg" chapters="00:00:00.000,00:01:36.000,00:02:00.479,00:03:00.479,00:04:24.479,00:05:47.520,00:06:21.120,00:08:29.760,00:11:23.040,00:14:37.919,00:15:39.360,00:18:40.799,00:20:51.360,00:21:48.959" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-7.mpg" chapters="00:00:00.000,00:01:36.000,00:02:52.319,00:03:55.200,00:04:58.560,00:07:47.520,00:10:42.720,00:12:37.439,00:13:55.680,00:15:04.320,00:16:43.680,00:18:13.680,00:19:32.159,00:20:51.840,00:21:48.959" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-8.mpg" chapters="00:00:00.000,00:01:36.000,00:02:02.400,00:03:47.520,00:05:22.559,00:07:49.919,00:11:57.599,00:13:00.959,00:14:05.880,00:17:37.439,00:19:20.280,00:20:51.840,00:21:49.200" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-9.mpg" chapters="00:00:00.000,00:01:36.000,00:02:16.799,00:04:20.159,00:07:31.200,00:08:17.760,00:09:18.719,00:10:16.799,00:14:18.719,00:15:35.520,00:18:04.320,00:20:50.880,00:21:49.319" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=1; </pre>
    <vob file="/media/storage/DVD-Root/bleach-10.mpg" chapters="00:00:00.000,00:01:36.000,00:02:23.280,00:03:30.719,00:05:08.159,00:08:02.880,00:11:04.800,00:14:18.719,00:16:46.080,00:18:38.400,00:19:46.080,00:20:50.880,00:21:48.959" />
    <post> g3=1; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-11.mpg" chapters="00:00:00.000,00:01:36.000,00:03:32.639,00:04:37.439,00:05:53.279,00:08:01.919,00:09:09.600,00:11:24.000,00:13:37.919,00:15:46.080,00:18:13.920,00:19:54.720,00:20:51.840,00:21:49.439" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-12.mpg" chapters="00:00:00.000,00:01:36.000,00:03:27.840,00:05:09.600,00:07:21.120,00:08:35.520,00:09:58.080,00:10:47.040,00:12:45.599,00:16:31.200,00:20:25.440,00:20:51.360,00:21:48.959" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-13.mpg" chapters="00:00:00.000,00:01:36.000,00:02:14.399,00:04:18.239,00:06:00.000,00:07:03.360,00:09:09.119,00:11:09.600,00:15:40.319,00:16:36.000,00:17:44.639,00:19:25.920,00:20:51.840,00:21:49.439" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-14.mpg" chapters="00:00:00.000,00:01:36.000,00:02:36.479,00:03:00.000,00:05:04.320,00:07:38.400,00:10:40.799,00:11:49.439,00:13:24.000,00:15:00.000,00:15:48.479,00:18:10.056,00:20:46.560,00:21:44.400" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-15.mpg" chapters="00:00:00.000,00:01:36.000,00:03:13.439,00:04:35.520,00:06:25.920,00:08:51.360,00:10:26.399,00:11:05.760,00:11:39.360,00:13:10.560,00:15:41.279,00:16:36.479,00:18:40.319,00:19:39.360,00:20:47.040,00:21:44.520" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-16.mpg" chapters="00:00:00.000,00:01:36.000,00:01:51.360,00:03:42.720,00:05:42.720,00:07:43.200,00:09:56.159,00:10:41.759,00:14:01.440,00:15:04.320,00:15:44.400,00:18:00.959,00:20:46.560,00:21:44.159" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-17.mpg" chapters="00:00:00.000,00:01:36.000,00:02:31.200,00:03:45.599,00:06:14.880,00:08:13.439,00:09:47.040,00:10:29.280,00:12:41.759,00:14:08.640,00:14:39.840,00:15:39.840,00:17:13.439,00:20:46.560,00:21:44.800" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-18.mpg" chapters="00:00:00.000,00:01:36.000,00:04:17.280,00:05:02.880,00:07:02.400,00:07:28.319,00:09:44.159,00:11:10.560,00:13:48.959,00:15:17.280,00:16:01.919,00:18:31.200,00:20:47.040,00:21:44.639" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-19.mpg" chapters="00:00:00.000,00:01:36.000,00:02:53.279,00:03:26.879,00:06:53.759,00:08:51.840,00:10:48.479,00:11:48.959,00:15:05.280,00:16:45.119,00:18:31.200,00:19:58.080,00:20:47.040,00:21:44.400" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc>
    <pre> g3=2; </pre>
    <vob file="/media/storage/DVD-Root/bleach-20.mpg" chapters="00:00:00.000,00:01:36.000,00:01:53.759,00:03:32.159,00:06:38.400,00:09:54.240,00:10:36.000,00:11:31.200,00:13:35.040,00:15:31.200,00:17:50.880,00:20:00.000,00:20:47.040,00:21:44.279" />
    <post> g3=2; call menu; </post>
   </pgc>
   <pgc/>
  </titles>
 </titleset>
</dvdauthor>

```

---

### Post by John.Michael.Kane on 2005-11-01
This may help [http://dvdauthor.sourceforge.net/](http://dvdauthor.sourceforge.net/)

---

