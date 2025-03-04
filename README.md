![Main Image Of Spectral](/img/main.png)

_This is an automated fork/mirror of the Spectrum3D Project over at: [http://spectrum3d.sourceforge.net/screenshots.html](http://spectrum3d.sourceforge.net/screenshots.html)_
_I am making a copy just in case it somehow disappears since it's a small piece of software that I love and would like to keep forever._
_Please support the original creators and thank you! 💕_

# What is Spectrum3d?

Spectrum 3D displays a 3D audio spectrogram in real time or not from the microphone or an audio file (including recorded file from the microphone); it is compatible with Jack (jack-audio-connection-kit). Optionally, it supports multitouch gestures from touchscreen and touchpad.

It is build with the Gstreamer, SDL (or Gtkglext), OpenGl, GTK+-2.0 and uTouch-Geis free libraries and is under GPL license. It is written for Ubuntu but works for other Linux distributions except for the multitouch frame (the uTouch suite is now available for Ubuntu).

Spectrum3d can be compiled against GTK2 or GTK3. SDL will be used as the OpenGL extension by default untill GtkGlExt has a stable release for GTK3 (however, GtkGlExt can be used already in Spectrum3d, including the development version (GTKGLEXT3 for GTK3), but this has to be specifically enabled at the time of compiling).


![Example 1](/img/spectrum3d_1.jpg)


![Example 2](/img/spectrum3d_2.jpg)


![Example 3](/img/spectrum3d_3.jpg)


![Example 4](/img/spectrum3d_4.jpg)


![Example 5](/img/spectrum3d_5.jpg)


![Example 6](/img/spectrum3d_6.jpg)
SPECTRUM 3D: 3D AUDIO SPECTRUM ANALYSER IN REAL TIME

Spectrum 3D displays a 3D audio spectrogram in real time; the source can be either the microphone or an audio file; it is also possible to record a file and to have it analysed; so analysis can be done done on the fly (harmonics are displayed while the audio file is being played), or before the file is being played (in that case, the analysis of the whole will be performed and displayed, then the file can be played afterwards). It is compatible with jack (jack-audio-connection-kit). Optionally, it supports multitouch gestures from touchscreen. It is build with the Gstreamer, SDL 1 or 2, OpenGl, GTK2 or GTK3 and is under GPL license. It is written for Ubuntu but works for other Linux distributions. 

Spectrum3d can be compiled against GTK2 or GTK3, against Gstreamer0.1 or Gstreamer1 and against SDL 1 or SDL2. Multitouch is now handled entirely by SDL2.

*******************
|  INSTALLATION:  |
*******************

1. dependencies:
""""""""""""""""
FOR UBUNTU from 10.10 : All dependencies are available in the Ubuntu repositories.

		- gcc, pkg-config, automake;
		- libgtk-2.0-dev or libgtk-3.0-dev;
		- libgstreamer0.10-dev or libgstreamer1.0-dev;
		- libsdl2-dev or lidsdl1.2-dev;
		- gstreamer1.0-plugins-base and gstreamer0.10-plugins-good at least for GSTREAMER1.0; gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly et gstreamer0.10-plugins-ugly-multiverse (for reading files such as mp3);

	For JACK support : 
		- (optional) libjack-dev (for jack1) or libjack-jackd2-dev for jack2; 

		  
FOR OTHER DISTRIBUTIONS : 
	For the other distributions, the dependencies should be very similar. 

2. compilation and installation : 
"""""""""""""""""""""""""""""""""
 	1) in a terminal, go to the directory where the sources are; for example, if the source package is in the HOME directory :

		$ cd ~/spectrum3d-<the-actual-version> (if the sources are in the "home" directory);

	2) type : 

		$ ./configure 

Libraries used by default are the latest : GTK 3, Gstreamer-1.0 ans SDL2. If not present, an older version of those will be searched. If you have both an older an d a newer version of GTK or SDL  library  installed and want the older version used, you can do this by typing :

		$ ./configure --enable-gtk2 

	or 

		$ ./configure --disable-gtk3

for GTK 2 instead of GTK3

		$ ./configure --enable-sdl 

	or 

		$ ./configure --disable-sdl2

for SDL 1 instead of SDL2	
	
NOTE for JACK SUPPORT:
	If Jack library is found, JACK support will be enabled. Both jack and jack2 are supported.However, jack support can be disabled by typing :
	
		$ ./configure --disable-jack 


	You can combine several arguments. For example :

		$ ./configure --disable-gtk3 --disable-jack

	If you want Spectrum3d to be installed in another directory than the default one ('/usr/local/bin'), you can add it at 'configure' step according to the 'Autoconf' standards. For example : 

		$ ./configure --prefix=/usr

will install the executable 'spectrum3d' file in '/usr/bin' directory instead of '/usr/local/bin'. 

	3) type :

		$ make

	4) type : 

		$ sudo make install (the password will be necessary for this)

	5) to completely remove Spectrum3d, type :

		$ sudo make uninstall


*********
|  USE  |
*********

Type in a terminal : 

	$ spectrum3d

or run it from 'Menu->Applications->Sound & Video->Spectrum3d'

The 2 most important things to do first are :
			- to select the type of audio source : either microphone or audio file; microphone is the default;
			- set if analyse will be done in real time or not : if 'analyze in real time' is checked, harmonics will be retrieved and displayed on the fly, while the sound is being played; if 'Analyse in real time' is unchecked, harmonics of the whole audio file will be retrieved and displayed first, then the file can be played afterwards. When source is set to microphone and 'Analyse in real time' is unchecked, recording can be made; it will be analysed and displayed like for an audio file; similarly it can be also played afterward. 

The 'reload' button allows to reload (i.e. analyse and display its harmonics) without reselecting the file.

You can record from the microphone and have the generated audio file analysed and displayed by selecting 'microphone' as the audio source, then unchecking the 'analyse in real-time' button; then the record button will be usable; a 'record window' will then pop up; after recording, a click on 'OK' will load the file as for an audio file. 

If 'Use JACK' is checked, everything explained above can be done with Jack (Jack-Audio-Connection-Kit).

Another window that commands different filters can be displayed :
- a 10 bands equalizer; the filtered frequencies and their range can be adjusted; the amplification goes from -72dB to +36dB;
- a band-reject or band-pass filter;

The lowest displayed frequency is 0 Hz by default, and it can be increased. The default range is 2000 Hz. It can be decreased to 40 Hz or raised to 20000Hz. To change this, you can either change it by using the 'Range of Display' scale, or increase it by changing the factor that is on its right : this factor multiplies the frequency range. The smallest possible step between 2 analyzed and displayed frequencies is 2 Hz.

From the menu : 
	* you can choose between 3 types of view :  - a 3D view that shows frequency, intensity and time; It is possible to rotate or translate the display along the X, Y and Z axis, either by keyboard commands, or by mouse (+/- keyboard) commands, or by touch gestures (if enabled). All the analyzed values are kept in memory, which implies that even if zoom or perspective changes, any value can be retrieved at any time, even when playing is paused.
					   - a 2D 'flat' view : that shows time versus frequency; the intensity however is represented by the amount of red color;
					   - a 3D 'flat' view that is somehow a compromise between the two previous views.

	* the perspective can be reset, set to a 'front' view (frequency versus intensity), or set to values preset by the user. The text can be displayed or not, as well as the line scale. A 'pointer' can be displayed, showing a location on the scale and its exact numerical value as well as the intensity of the frequency (fot the 3D view).

	* you can chose to display text and lines or not and also a pointer that will point to a specific frequency; it will display it frequency value, and for the 3D perspective its intensity value;

	* you can play a test sound which is a sine wave from 1 to 20000 Hz;

	* you can set, in 'preferences' : 
		- the distance between frames : the biggest this value is, the 'deeper' the image will go;
		- the number of displayed frames, the biggest this value is, the 'deeper' the image will go and the more cpu will be used;
		- the interval of time (in milliseconds) between each refreshing of the display; the smallest this value will be, the nicer the display will look, but the more demanding it will be on the cpu; every change in this will require Spectrum3d to be restarted to be effective;
		- the color of the display (when analyse in real-time is selected);
		- whether you want that the actual display is saved as preset;
		- the interval of time (in milliseconds) between each new analysis of the spectral data; as for display, the smallest this value will be, the more demanding it will be on the cpu; this value should match the interval of time between 2 displays for better display but this is not mandatory.
		- the activation of multitouch gestures commands (activated by default);

	All those preferences are kept in a 'preferences' file that is created at first use of Spectrum3d and placed in the home directory : ~/.spectrum3d/spectrum3d.pref. Everytime Spectrum3d starts, it check some values of this 'preferences' file for consistency; if out of range value is found, a new 'preferences' file with default values is created.


You'll find below a summary of the keyboard, mouse and gestures commands. 

KEY AND MOUSE BINDINGS :
"""""""""""""""""""""""""""""""""	
Some commands are possible by keyboard or keyboard and mouse combination.

Command	                        Keyboard                      Mouse (+/-keyboard)
================================================================================================================================
Play/pause                      Space bar
Stop			        Escape
Rotate around X axis            Up/down                       Left click + Mouse up/down
Rotate around Y axis            Right/left                    Left click + Mouse right/left
Rotate around Z axis            SHIFT + Up/down               Left click + mousewheel up/down
Translate along X axis          CTRL + left/right             Right click + mouse right/left
Translate along Y axis          CTRL + up/down                Right click + mouse up/down
Translate along Z axis          CTRL + SHIFT + up/down        Mousewheel up/down
Change starting value
  of the display                ALT + left/right	      X + mouse right/left (diagonal movement 
                                                              make it change much faster)
Change starting value
  of the display 
  (bigger steps)                X + left/right		
Change range of the 
  display                       ALT + up/down                 C + mouse right/left (diagonal movement 
                                                                                                                         make it change much faster)
Change range of the 
  display (bigger steps)	X + up/down
Increase/decrease Gain          G + up/down		
Move pointer up/down            Q + right/left
Move pointer up/down
    (fast)                      A + right/left
Show/hide frequency             T
Show/hide lines                 L
Show/hide pointer               P
Reset view                      R
Front view                      O

GESTURES COMMANDS :
"""""""""""""""""""	

Command	                        Gesture		
=======================================================================
Play/pause                      Double Tap
Rotate around X axis            1 finger Drag Up/down	
Rotate around Y axis            1 finger Right/left
Rotate around Z axis            2 (or more) fingers Rotate
Translate along X axis          2 (or more) fingers Right/left
Translate along Y axis          2 (or more) fingers Drag Up/down
Translate along Z axis          2 (or more) fingers Pinch
Change starting value 
of display                      Touch lower left corner + move the other finger right/left
                                X + Touch right/left
                                (diagonal movement make it change much faster)
Change range of display         Touch upper left corner + move the other finger right/left
                                C + Touch right/left
                                (diagonal movement make it move much faster)


**********
| NOTES  |
**********

1. Although it is 3D with OpenGL, the drivers for 3D acceleration are not needed (no need for proprietary drivers here!), but it can help to have a better rendering. 

2. Spectrum 3D can use a lot of resources on your machine, given the real-time analysis and 3D display of the data's. 3 aspects are important : the power of the processor, the performance of the graphic card (with or without the 3D drivers) and the type of kernel that is being used (a preempt or real-time will allow better performance). The amount of needed resources is proportional to the width of the window. If your machine has difficulty, you can use a smaller window size. However, given the increased capabilities of computers, those precautions are now to be taken on old computers (or very basic models).


Thank you for your feedback and than you for your presence!

Victor 
nadaeck (at) hotmail (dot) com	


<a href="https://s3-us-west-2.amazonaws.com/web-portfolio-static/pages/3dspectro/index.html">Project website</a>

