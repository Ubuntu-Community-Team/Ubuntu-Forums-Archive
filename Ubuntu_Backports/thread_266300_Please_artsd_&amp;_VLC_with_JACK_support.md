---
title: "Please: artsd &amp; VLC with JACK support"
date: 2006-09-27
forum: Ubuntu Backports
---

### Post by scotty64 on 2006-09-27
The fact that artsd does not have a jack-plugin in Ubuntu is a huge setback. The same applies to the latest VLC packages (0.8.5) that does not support the jack-output that is part of the official VLC source package.
I would highly appreciate a general "Ubuntu guideline" saying:
If an audio application supports JACK, then build the package jack-enabled by default.

---

### Post by ankara on 2006-11-14
i agree this is REALLY annoying. 
im currently having to wade through installing the libs required to compile my own build of VLC with jack support.
i find that in linux more than in windows theres no limiting on the output of the audio and so i get clipping if the volumes on both alsa mixer and whatever audio software im using at the time arent ballanced perfectly.
ardour is ok as i can use meterbridge with jack for the master etc. 
i need that same control on a daily basis. 
](*,) ](*,) ](*,) ](*,) ](*,)

an explination from a developer or someone in the ubuntu team would be nice ....... please.....

---

### Post by Scott Carlson on 2007-12-20
Same here in Ubuntu 7.10.  I wanted to use jackd with skype to change my voice on the phone.  I found an article to do it but found no jackd support in artsd to make it possible.  I am now trying to compile artsd and am now having problems with libraryies not found.  Hope they fix this soon.

---

### Post by scotty64 on 2007-12-21
> **Scott Carlson said:**
> Same here in Ubuntu 7.10.  I wanted to use jackd with skype to change my voice on the phone.  I found an article to do it but found no jackd support in artsd to make it possible.  I am now trying to compile artsd and am now having problems with libraryies not found.  Hope they fix this soon.

Hi Scott,
I discovered that after a lot of bad ALSA implementations the latest Skype for Linux has more or less proper ALSA support. Foreget trying with artsd - a dead application anyway and the struggle with oss2jack and kernelmodules. You can use a simple .asoundrc file to connect Skype to jackd and whatever jackd application you like now. I use the example file below to connect it to my Presonus Firebox firewire audio interface. I have even  used the Firebox, Ubuntu, Skype, Jackd, Ardour and Oddcast to do live mixing of Skype calls with several mikes, a PA system and broadcast the whole over the internet. It works excellent!
But I have to admit here that I am always using the latest jackd from SVN and I have not tried the Ubuntu "native" jackd for a long time as it did not have the freebob ports in dapper.
About .asoundrc:
Do not forget to use the right names for the capture and playbackports (jack_lsp lists all currently defined ports on your system).
Start Skype after you have installed the .asoundrc in your home directory. You should now be able to choose a "jack" device within Skypes audio device settings.
 I use the following command (via Qjackctl) to start jackd with freebob support and proper skype audio:
jackd -R -p1024 -dfreebob -r48000 -p512 -n3 -i1 -o1
Just uncomment the first lines in the following .asoundrc listing  if you would like to use the jackd-device as default device:

#pcm.!default {
#       type plug
#       slave { pcm "jack" }
#}

pcm.jack {
        type jack
        playback_ports {
                0 "system:playback_1"
                1 "system:playback_2"
        }
        capture_ports {
                0 "system:capture_1"
                1 "system:capture_2"
        }
}

#ctl.mixer0 {
#       type hw
#       card 0
#}

---

### Post by kleinebre on 2008-06-14
> **ankara said:**
> i agree this is REALLY annoying. 
im currently having to wade through installing the libs required to compile my own build of VLC with jack support.

And to think that JACK support can be compiled in, even if JACK is not available.

jackwrapper.h

#include <jack/jack.h>
class JackWrapper {
  void* libhandle;
public:
  jack_client_t* (*jack_client_new)(const char*);
  int (*jack_set_process_callback)(jack_client_t*,JackProcessCallback,void*);
  void (*jack_on_shutdown)(jack_client_t*,void (*function)(void *), void *);
  jack_nframes_t (*jack_get_sample_rate)(jack_client_t*);
  void* (*jack_port_get_buffer)(jack_port_t*,jack_nframes_t);
  jack_transport_state_t (*jack_transport_query)(const jack_client_t*,jack_position_t*);
  jack_port_t* (*jack_port_register)(jack_client_t*,const char*,const char*,unsigned long,unsigned long);
  int (*jack_activate)(jack_client_t*);
  jack_nframes_t (*jack_get_current_transport_frame)(const jack_client_t*);
  int (*jack_transport_locate)(jack_client_t*,jack_nframes_t);
  void (*jack_transport_start)(jack_client_t*);
  void (*jack_transport_stop)(jack_client_t*);
  void define_functions(void* handle);
  JackWrapper();
  ~JackWrapper();
};

jackwrapper.cpp

#include <jackwrapper.h>

void JackWrapper::define_functions(void* handle) {
  if (handle==NULL) return;
libhandle=handle;
// Given a handle to a dynamic library, define functions that are in it.
jack_client_new=(jack_client_t*(*)(const char*))dlsym(handle,"jack_client_new");
jack_set_process_callback=(int(*)(jack_client_t*,JackProcessCallback,void*))dlsym(handle,"jack_set_process_callback");
jack_on_shutdown=(void (*)(jack_client_t*,void (*function)(void *), void *))dlsym(handle,"jack_on_shutdown");
jack_get_sample_rate=(jack_nframes_t (*)(jack_client_t*))dlsym(handle,"jack_get_sample_rate");
jack_port_get_buffer=(void* (*)(jack_port_t*,jack_nframes_t))dlsym(handle,"jack_port_get_buffer");
jack_transport_query=(jack_transport_state_t (*)(const jack_client_t*,jack_position_t*))dlsym(handle,"jack_transport_query");
jack_port_register=(jack_port_t* (*)(jack_client_t*,const char*,const char*,unsigned long,unsigned long))dlsym(handle,"jack_port_register");
jack_activate=(int (*)(jack_client_t*))dlsym(handle,"jack_activate");
jack_get_current_transport_frame=(jack_nframes_t (*)(const jack_client_t*))dlsym(handle,"jack_get_current_transport_frame");
jack_transport_locate=(int (*)(jack_client_t*,jack_nframes_t))dlsym(handle,"jack_transport_locate");
jack_transport_start=(void (*)(jack_client_t*))dlsym(handle,"jack_transport_start");
jack_transport_stop=(void (*)(jack_client_t*))dlsym(handle,"jack_transport_stop");
}

JackWrapper::JackWrapper() {
  jack_client_new=NULL;

// TODO: use smart path lookup instead of hard coded

void* handle=dlopen("/usr/lib/libjack.so",RTLD_NOW);
if (handle==NULL) {
        cout << dlerror() << endl;
} else {
        define_functions(handle);
}
}

JackWrapper::~JackWrapper() {
  dlclose(libhandle);
}

This allows looking up (and using) the library in runtime, so jack
support can be compiled in at all times, and if it is not available on the machine of the user, the application could work around it by using portaudio or something.

---

