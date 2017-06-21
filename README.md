# smart-resize

A utility for resizing image to the largest possible size, given a certain aspect ratio. Images are either cropped to fit the aspect ratio, or can be increased a long a certain direction. If the image is expanded, the most common color along the image's edge is used to fill in the new backgroudn. 

## Installation

`smart-resize` uses ImageMagick under the hood, and thus ImageMagick must be [installed](http://imagemagick.org/script/download.php) first. 

## Usage

ImageMagick must be installed for `smart-resize` to work. 
Simply run the script as follows:

```
sh smart-resize shrink|expand|exact -a <width>x<height> -g <gravity> <input_image> <output_image> 
```

### Commands:

The `smart-resize` script has three command: `shrink`, `expand`, and `exact`. The syntax is:

* *shrink* crops an image to the given aspect ratio, but ensures that the resulting area is as large as possible, i.e. preserves either the full height or width of the image. 

* *expand* also preserved either the full height or width of the image, but then expands the other dimension to match the given aspect ratio. The new areas in the image are filled in with the most common color along the edge that is being expanded. 

* *exact* merely crops the image to the exact resolution given. 

### Arguments: 

* The aspect ratio is specified using the `-a` flag. The argument is `WIDTH`x`HEIGHT`, where WIDTH and HEIGHT are integers. This represents the desired aspect ration of the resuling image, or the exact dimensions if the `exact` command is used. 

* The direction in which to expand or shrink an image is specified by the `-g` (or "gravity") flag. The "gravity" specified the direction in which the original image is placed relative to the new image. For example, to only expand the image along the top, you'd want `-g south`. This is the same as IamgeMagick's `gravity` flag, and more documentation can be found [here](https://www.imagemagick.org/script/command-line-options.php#gravity).
