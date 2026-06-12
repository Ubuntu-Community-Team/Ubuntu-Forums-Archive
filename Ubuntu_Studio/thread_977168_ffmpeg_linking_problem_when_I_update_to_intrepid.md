---
title: "ffmpeg linking problem when I update to intrepid"
date: 2008-11-09
forum: Ubuntu Studio
---

### Post by Wilberth R. Garcia Alfaro on 2008-11-09
First all sorry if this is not the rigth place to ask for, but my problem is this:

I have an application that works with QT 4.4.3 Phonon ffpmeg and opencv frameworks. My application was working fine until I update to Intrepid and since Intrepid uses a new version of ffmpeg (hardy has a version from 2007) i cant compile my new version of this application. I tried compiling a svn version of ffmpeg but it did not for me. I am sure that this version of ffmpeg is the problem because my applicación can compile in other machines with hardy heron and the old ffmpeg version. 
Here is the message I got for when I try to compile:

/usr/bin/qmake -unix -o Makefile Proyecto.pro
g++ -Wl,--no-undefined -o bin/Proyecto compilar/mainwindowimpl.o compilar/main.o compilar/Cords.o compilar/moc_mainwindowimpl.o compilar/qrc_proyecto.o    -L/usr/lib /usr/lib/libavcodec.so /usr/lib/libcv.so /usr/lib/libcxcore.so /usr/lib/libhighgui.so -lphonon -lQtGui -lQtNetwork -lQtCore -lpthread
compilar/mainwindowimpl.o: In function `MainWindowImpl::btnVideoEvent()':
/home/richgar1982/Proyecto/src/mainwindowimpl.cpp:186: undefined reference to `avcodec_init()'
/home/richgar1982/Proyecto/src/mainwindowimpl.cpp:188: undefined reference to `avcodec_register_all()'
compilar/mainwindowimpl.o: In function `Video::CodecMpgVideo(CodecID)':
/home/richgar1982/Proyecto/src/Vid.h:51: undefined reference to `avcodec_find_encoder(CodecID)'
compilar/mainwindowimpl.o: In function `Video::CreateAVFrame(unsigned int)':
/home/richgar1982/Proyecto/src/Vid.h:64: undefined reference to `avcodec_alloc_frame()'
compilar/mainwindowimpl.o: In function `~Video':
/home/richgar1982/Proyecto/src/Vid.h:29: undefined reference to `avcodec_close(AVCodecContext*)'
compilar/mainwindowimpl.o: In function `void Video::InsertVideoFrames<_IplImage*, std::deque>(std::basic_ofstream<char, std::char_traits<char> >&, std::deque<_IplImage*, std::allocator<_IplImage*> >&)':
/home/richgar1982/Proyecto/src/Vid.h:177: undefined reference to `avcodec_encode_video(AVCodecContext*, unsigned char*, int, AVFrame const*)'
compilar/mainwindowimpl.o: In function `void Video::MakeVideo<_IplImage*, std::deque>(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::deque<_IplImage*, std::allocator<_IplImage*> >)':
/home/richgar1982/Proyecto/src/Vid.h:115: undefined reference to `avcodec_alloc_context()'
/home/richgar1982/Proyecto/src/Vid.h:124: undefined reference to `avcodec_open(AVCodecContext*, AVCodec*)'
/home/richgar1982/Proyecto/src/Vid.h:146: undefined reference to `avcodec_encode_video(AVCodecContext*, unsigned char*, int, AVFrame const*)'
collect2: ld devolvió el estado de salida 1
make: *** [bin/Proyecto] Error 1

Please help me i cant find where the problem is ...!!! It seems that the libavcodec.so is not on my /usr/lib directory but it is there, maybe gcc cant find the implementation of those functions buts they should be there in the libavcodec.so file.

Thakns

---

### Post by nowardev on 2008-11-10
sorry you wanna compile ffmpeg or what? 

maybe this should explain something about ffmpeg i dunno if this could help you anyway

[http://www.nowardev.netsons.org/?q=node/12](http://www.nowardev.netsons.org/?q=node/12)

---

### Post by Wilberth R. Garcia Alfaro on 2008-11-10
Hi thanks for your reply, let me explain:

I have a application  I wrote in c++ using things like QT ffmpeg and opencv (this is my homework for programing subject) but when I updated my ubuntu to intrepid it updated a ffmpeg libraries. From theses moment I can't compile my applicaction because g++ can't found a libavcodec.so file. But the file is in /usr/lib. I want to know if libavcodec.so has not the implementation for these functions or what can I do to compile theses application.

---

### Post by nowardev on 2008-11-11
well i hate ffmpeg developers and packagers  i really prefer mencoder and your problem is the demonstration that what i think is correct FFmpeg is a ****

the problem is this:

 if before the name of codec was aac now with  the new ffmpeg it's libfaac ... as you can figure out if you have made a program the changing of ffmpeg commmand line has lead at several problems... 

another problem now it's the different way medibuntu packagers has choosen to pack  ffmpeg 

if before you had to add medibutu repository and ther reinstall ffmpeg now you have to do that and more you have to install a lots of packages to fix your ffmmpeg.

**so if you want know why** your application doesn't work you should see the code or ask to developer and this is the real **** of ffmpeg 
 
an idea i am on hardy and the name of this library is 

/usr/lib/libavcodec.so.1d

maybe on intrepid there is this library but it has changed name ... ehm you could try to rename but ... for me this a complete disaster for several application what i can say....

sorry i can't help you more

---

### Post by ekansdiuqil on 2008-12-17
I have nearly the same problem. When I tried to use the opencv cvCreateVideoWriter function it gives error and my program aborts. I nearly tried to write the codecs in this function that opencv support. I even tried raw video.(codec as 0). 

Also this function had no problems with hardy heron.

---

