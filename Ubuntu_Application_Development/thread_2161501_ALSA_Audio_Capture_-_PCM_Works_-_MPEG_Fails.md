---
title: "ALSA Audio Capture - PCM Works - MPEG Fails"
date: 2013-07-10
forum: Ubuntu Application Development
---

### Post by LightOfSolomon on 2013-07-10
I picked up the sample ALSA code below from Linux Journal and it works fine for outputting PCM audio format. However, I would like to change the capture format to SND_PCM_FORMAT_MPEG to make it easier to stream audio to remote clients without having to do any audio conversion. I have been unsuccessful in figuring out how to change the capture format to MPEG. Has anyone sucessfully used this mode in any ALSA development? 

Compile: gcc alsatest.c -lasound

Execute: ./alsatest >sample.pcm 

You can import and play the raw audio using audacity.  Again, the PCM mode works great... I can't figure out how to write directly to MPEG. :confused:

/*

Source: Linux Journal - [http://www.linuxjournal.com/node/6735/print](http://www.linuxjournal.com/node/6735/print)
Example 4 - Simple sound recording

This example reads from the default PCM device
and writes to standard output for 5 seconds of data.

*/

/* Use the newer ALSA API */
#define ALSA_PCM_NEW_HW_PARAMS_API

#include <alsa/asoundlib.h>
#include <stdio.h>

int main() {
  long loops;
  int rc;
  int size;
  snd_pcm_t *handle;
  snd_pcm_hw_params_t *params;
  unsigned int val;
  int dir;
  snd_pcm_uframes_t frames;
  char *buffer;
  

  /* Open PCM device for recording (capture). */
  rc = snd_pcm_open(&handle, "default",
                    SND_PCM_STREAM_CAPTURE, 0);
  if (rc < 0) {
    fprintf(stderr, 
            "unable to open pcm device: %s\n",
            snd_strerror(rc));
    exit(1);
  }
  
  /* Allocate a hardware parameters object. */
  snd_pcm_hw_params_alloca(&params);

  /* Fill it in with default values. */
  snd_pcm_hw_params_any(handle, params);

  /* Set the desired hardware parameters. */

/*
if( snd_pcm_hw_params_test_format( handle, params, SND_PCM_FORMAT_MPEG ) >= 0)
{
   printf("Doh!");
}
*/

//exit(0);

  /* Interleaved mode */
  snd_pcm_hw_params_set_access(handle, params,
                      SND_PCM_ACCESS_RW_INTERLEAVED);



  /* Signed 16-bit little-endian format */
  snd_pcm_hw_params_set_format(handle, params,
                              SND_PCM_FORMAT_S16_LE);

  /* Two channels (stereo) */
  snd_pcm_hw_params_set_channels(handle, params, 2);

  /* 44100 bits/second sampling rate (CD quality) */
  val = 44100;
  snd_pcm_hw_params_set_rate_near(handle, params, 
                                  &val, &dir);

  /* Set period size to 32 frames. */
  frames = 32;
  snd_pcm_hw_params_set_period_size_near(handle, 
                              params, &frames, &dir);

  /* Write the parameters to the driver */
  rc = snd_pcm_hw_params(handle, params);
  if (rc < 0) {
    fprintf(stderr,
            "unable to set hw parameters: %s\n",
            snd_strerror(rc));
    exit(1);
  }

  /* Use a buffer large enough to hold one period */
  snd_pcm_hw_params_get_period_size(params,
                                      &frames, &dir);
  size = frames * 4; /* 2 bytes/sample, 2 channels */
  buffer = (char *) malloc(size);

  /* We want to loop for 5 seconds */
  snd_pcm_hw_params_get_period_time(params,
                                         &val, &dir);
  loops = 5000000 / val;

  while (loops > 0) {
    loops--;
    rc = snd_pcm_readi(handle, buffer, frames);
    if (rc == -EPIPE) {
      /* EPIPE means overrun */
      fprintf(stderr, "overrun occurred\n");
      snd_pcm_prepare(handle);
    } else if (rc < 0) {
      fprintf(stderr,
              "error from read: %s\n", 
              snd_strerror(rc));
    } else if (rc != (int)frames) {
      fprintf(stderr, "short read, read %d frames\n", rc);
    }
    rc = write(1, buffer, size);
    if (rc != size)
      fprintf(stderr, 
              "short write: wrote %d bytes\n", rc);
  }

  snd_pcm_drain(handle);
  snd_pcm_close(handle);
  free(buffer);

  return 0;
}

---

### Post by tgalati4 on 2013-07-11
I would use *arecord* and *lame* and pipe them together:  (you would have to refine the syntax)

arecord myrecordedpcmfile.pcm | lame myrecordedpcmfile.mp3

The article is from 2004, so I would expect some changes to the ALSA framework, so you need to be mindful of that.  As a general rule, you need to install *lame* and use the *lame* mp3 libraries to record to mp3.  There are licensing issues with recording to mp3, so you need to be aware of that as well.

---

### Post by LightOfSolomon on 2013-07-11
Thanks for your help Tgalati4! That works for now. Eventually, I would like to have self-contained code to handle this task.

---

### Post by tgalati4 on 2013-07-11
You can look at the source code for *arecord* and *lame* and cut-and-paste the interesting parts.

---

