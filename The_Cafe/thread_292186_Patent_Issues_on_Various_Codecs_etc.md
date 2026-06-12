---
title: "Patent Issues on Various Codecs etc"
date: 2006-11-03
forum: The Cafe
---

### Post by musther on 2006-11-03
I saw this story on slashdot last night:

[http://yro.slashdot.org/article.pl?sid=06/11/02/2254224&from=rss](http://yro.slashdot.org/article.pl?sid=06/11/02/2254224&from=rss)

At first it seems quite interesting, but after reading all the comments and doing a little research it seems that their claim on JPEG is tenuous at best.

But it makes me think about the other codecs and such that we use, and either are, or or not allowed to include in Ubuntu (by default).  WMV (windows media video) is a classic example, the only way to use it is to download the dll's from wherever.  But how about PDF, is it a free open format, how about Microsoft's DOC?  

I'm not even quite sure how it works, if a codec is patented, does that simply mean we can't include it, such as with MP3?  Or, if some boffin managed to reverse-engineer WMV and create 'libwmv', would we be able to include that as it would be our own implementation?  

Can somebody enlighten me?

---

### Post by DoctorMO on 2006-11-03
You are confuised between copyright and patents.

firstly using the wmv dlls outside of windows is a copyright violation even if you have a windows licence because the terms say you cann't use these components outside of the windows enviroment.

we have a free mp3 codec distrobuted under copy left.

the seond thing is patents, patents only exist on methods NOT on formats, things or code. if you can decode an mp3 without using any of the methods described in their patents your home and dry. same goes for any patents related to wmv.

The problem is that software patents have been granted to very large general ideas and methods. so a wmv patent may hurt a calculator app if it uses one of those methods.

The best thing to do is to distrobute regardless of patents. not to break copyright by using dlls and reverse engeneering the formats (we can't use the documents on msdn because they have too restrictive terms) if they sue then you can invalidate the patent. but I dout most companies will sue pennyless developers as patents can only be used against those that use the methods described not those who use the products there after. (unlike copyrights)

PDF, adobe has some patents on methods used in pdf but has terms which state that they won't use those patents against anyone that follows their open and available specification.

---

### Post by EdThaSlayer on 2006-11-03
I guess that this is the reason Ubuntu doesn't come with all the codecs installed, many are from these huge greedy companies, so you can get sued for having the codec for .avi for example...*looks at DoctorMo's reply* I guess iam right...Ubuntu would get sued if it included those proprietary drivers and codecs...

---

### Post by musther on 2006-11-03
Thanks for that, very insightful.  :)

---

### Post by DoctorMO on 2006-11-03
ubuntu could be sued by Microsoft for including dlls, but I don't think it could for including the MP3 codec, since it's FOSS. the patents should be disregarded. (I can't wait until 2015 when mp3 patents run out)

---

### Post by mdsmedia on 2006-11-03
> **DoctorMO said:**
> ubuntu could be sued by Microsoft for including dlls, but I don't think it could for including the MP3 codec, since it's FOSS. the patents should be disregarded. (I can't wait until 2015 when mp3 patents run out)I doubt that the MP3 codec is FOSS. That's why it's NOT distributed with Ubuntu. It breaches licensing restrictions. Hence its inclusion in Automatix with warnings about the legality of installing the codecs in say the USA.

---

### Post by DoctorMO on 2006-11-03
[http://lame.sourceforge.net/about.php](http://lame.sourceforge.net/about.php) *yawn* LAME is the copy left mp3 encoder/decoder the reason why it can't be used in the USA without a stupid licence is because of patents.

Yet it's ok to distrobute FAT32 software, NTFS patent infringing software. it's totaly inconsistant. either you remove _all_ patented methods from your distrobution (and your looking at a really BAD OS when you do) or you keep FOSS code anyway because software patents must be removed.

We _should_ include the mp3 lame enc/dec in ubuntu precisly because it's FOSS.

---

### Post by jpeddicord on 2006-11-03
I believe ffmpeg will include WMV9 in the next version, but uses a different non-patented method to do this. That means no more w32codecs, since Quicktime support is in the repos also.

---

### Post by DoctorMO on 2006-11-03
that is good news! all we would need then in wmv10 and perhaps a foss drm version which is allowed under the compatability clauses in the DMCA. (although it would have to stay GPLv2 ;-))

---

