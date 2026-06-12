---
title: "compilar driver uvcvideo"
date: 2010-06-24
forum: Software
---

### Post by santiago79 on 2010-06-24
Hola gente, estoy tratando de solucionar un problema que tengo con mi webcam del un portatil asus que me da la imagen de cabeza
bueno resulta que buscando me encuentro que compilado el driver con un parche se soluciona entonces procedo a eso pero para sorpresa en el momento de hacer make me da un error
bueno entonces voy y lo hago son el parche el driver original y me sale lo mismo, alguien me puede ayudar? se los agradeceria mucho.


>  root@santiago-ubuntu:/home/santiago-ubuntu/trunk# make uvcvideo
Building USB Video Class driver...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/santiago-ubuntu/trunk/uvc_driver.o
/home/santiago-ubuntu/trunk/uvc_driver.c: In function &#8216;uvc_register_video&#8217;:[http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)
/home/santiago-ubuntu/trunk/uvc_driver.c:1491: warning: assignment from incompatible pointer type
  CC [M]  /home/santiago-ubuntu/trunk/uvc_v4l2.o
/home/santiago-ubuntu/trunk/uvc_v4l2.c: In function &#8216;uvc_v4l2_do_ioctl&#8217;:
/home/santiago-ubuntu/trunk/uvc_v4l2.c:986: warning: passing argument 1 of &#8216;v4l_compat_translate_ioctl&#8217; from incompatible pointer type
include/media/v4l2-ioctl.h:285: note: expected &#8216;struct file *&#8217; but argument is of type &#8216;struct inode *&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:986: warning: passing argument 2 of &#8216;v4l_compat_translate_ioctl&#8217; makes integer from pointer without a cast
include/media/v4l2-ioctl.h:285: note: expected &#8216;int&#8217; but argument is of type &#8216;struct file *&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:986: warning: passing argument 3 of &#8216;v4l_compat_translate_ioctl&#8217; makes pointer from integer without a cast
include/media/v4l2-ioctl.h:285: note: expected &#8216;void *&#8217; but argument is of type &#8216;unsigned int&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:986: error: too many arguments to function &#8216;v4l_compat_translate_ioctl&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c: In function &#8216;uvc_v4l2_ioctl&#8217;:
/home/santiago-ubuntu/trunk/uvc_v4l2.c:999: warning: passing argument 1 of &#8216;video_usercopy&#8217; from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected &#8216;struct file *&#8217; but argument is of type &#8216;struct inode *&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:999: warning: passing argument 2 of &#8216;video_usercopy&#8217; makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;unsigned int&#8217; but argument is of type &#8216;struct file *&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:999: warning: passing argument 4 of &#8216;video_usercopy&#8217; makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected &#8216;v4l2_kioctl&#8217; but argument is of type &#8216;long unsigned int&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c:999: error: too many arguments to function &#8216;video_usercopy&#8217;
/home/santiago-ubuntu/trunk/uvc_v4l2.c: At top level:
/home/santiago-ubuntu/trunk/uvc_v4l2.c:1097: error: &#8216;v4l_compat_ioctl32&#8217; undeclared here (not in a function)
make[2]: *** [/home/santiago-ubuntu/trunk/uvc_v4l2.o] Error 1
make[1]: *** [_module_/home/santiago-ubuntu/trunk] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [uvcvideo] Error 2
root@santiago-ubuntu:/home/santiago-ubuntu/trunk# 



LA GUIA QUE ESTOY SIGUIENDO CON EL PARCHE ES ESTA 
[http://ubuntuforums.org/showthread.php?t=838210](http://ubuntuforums.org/showthread.php?t=838210)

---

