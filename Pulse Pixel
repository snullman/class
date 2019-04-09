from microbit import *
import neopixel

num_pixels = 24
np = neopixel.NeoPixel(pin0, num_pixels)  # Setup the NP on pin0 with 24 pixels

# neopixel color palettes
red = [255, 0, 0]
green = [0, 255, 0]
blue = [0, 0, 255]
orange = [255, 40, 0]
yellow = [255, 150, 0]
purple = [180, 0, 255]
RGB = (red, green, blue)  # rgb palette
warm = (red, orange, yellow)     # warm palette
cool = (green, blue, purple)      # cool palette

# heart pulse sensor
milliseconds_per_Second = 1000  # Timing settings
Sampling_count = 5               # 5 samples per second
Sampling_Interval = int(milliseconds_per_Second / Sampling_count)
high_pulse = 550                 # pulse rate samples
low_pulse = 500
beat = False

samples_between_beats = 0  # Samples that occur between beats
def warm_visuals():
    for i in range(0, num_pixels):
        np[i] = warm   # Assign the current LED warm colors
        np.show()      # Display the current pixel data on the Neopixel strip
        sleep(100)

def cool_visuals():
    for i in range(0, num_pixels):
        np[i] = cool    # Assign the current LED cool colors
        np.show()       # Display the current pixel data on the Neopixel strip
        sleep(100)

while True:
    pulse = pin2.read_analog()                   # read pulse
    samples_between_beats += 1                   # indicate pulse on microbit

    if beat is False and (pulse > high_pulse):  # if pulse is >= 550
        beat = True
        warm_visuals()   # display warm colors

    if beat is True and (pulse < low_pulse):   # if pulse is <= 500
        beat = False
        cool_visuals()        # display cool colors
        sleep(100)
        samples_between_beats = 0   # reset counter of samples_between_beats

# output signal value to REPL
# scale by2 then subtract 1000 to use full y-range of Plot graph
pulse = 2*pulse - 1000
# print("({})".format(Signal))
print("({}, {})".format(pulse, samples_between_beats*10))
sleep(Sampling_Interval)   # pause between samples
