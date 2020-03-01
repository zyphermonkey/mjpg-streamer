# mjpg-streamer
Setup for installing mjpg-streamer and setting up cron to load it startup.  
The uvcdynctrl is for a Logitech C910

## Install Dependencies
```
sudo apt-get install cmake libjpeg8-dev
sudo apt-get install gcc g++
```

## Install mjpg-streamer
```
git clone https://github.com/jacksonliam/mjpg-streamer.git
cd mjpg-streamer
cd mjpg-streamer-experimental
make
sudo make install
```

## Install uvcdynctrl
`sudo apt-get install uvcdynctrl`

## Cron
```  
crontab -e
@reboot /usr/local/bin/mjpg_streamer -i "/usr/local/lib/mjpg-streamer/input_uvc.so -n" -o "/usr/local/lib/mjpg-streamer/output_http.so -p 8081 -w /usr/local/share/mjpg-streamer/www" -b && uvcdynctrl -s 'LED1 Mode' 0
```  

# Single Commands
**List UVC Cameras**  
`uvcdynctrl -l`  

**Disable Camera LED**  
`uvcdynctrl -s 'LED1 Mode' 0`  

**Run mjpg-streamer**  
`mjpg_streamer -i "/usr/local/lib/mjpg-streamer/input_uvc.so -n" -o "/usr/local/lib/mjpg-streamer/output_http.so -p 8081 -w /usr/local/share/mjpg-streamer/www" -b`  

