# jetson-nano-test
Playing with jetson-nano. 
This commande in order to test different function

#Test the webcam on usb

gst-launch-1.0 -v v4l2src device=/dev/video1 ! 'video/x-raw,width=640, height=480, framerate=30/1, format=YUY2' ! nvvidconv ! xvimagesink

#Recorder video

gst-launch-1.0 -v v4l2src device=/dev/video1 ! 'video/x-raw,width=640, height=480, framerate=30/1, format=YUY2' ! nvvidconv ! 'video/x-raw(memory:NVMM),format=NV12' ! omxh264enc ! qtmux ! filesink location=/home/aswin/Videos/test.mp4 -e

#Comnmand with darknet with webcam usb
./darknet detector demo cfg/coco.data cfg/yolov3.cfg yolov3.weights /dev/video1


#with tiny
./darknet detector demo cfg/coco.data cfg/yolov3-tiny.cfg yolov3-tiny.weights /dev/video1
