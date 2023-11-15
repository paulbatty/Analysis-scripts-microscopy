# Analysis-scripts-microscopy
Example scripts written by me for the analysis of confocal microscopy images

- cellpose_threshold_fields_directory
These scripts uses cellpose to threshold nuclei in a confocal section for a field of cells.

The scripts expect the images to be in tif format with three or four channels. The array needs to be read in differently if you have a single or two channel image. 

The function takes two inputs, an inpath containing all of the tif files to be analysed, which is passed to the function as a list, and an out directory where you want to save the final csv file. The 'threshold_field' function iterates over all images in the in directory, uses the DNA channel to threshold individual nuclei using cellpose and generates a series of cell masks, which are then added to the channels of interest as labels. Additional parameters have been added in this script, for example 'remove_borders' from skimage which removes any mask which touches the border of the image. A size filter has also been specified in order to remove debris/very small cells/mitotic cells, which are not of interest in this analysis. The mean fluorescence intensity for the channels of interest is then calculated for the segmented nuclei and output as a csv file.

A second function, plot_images, allows you to visualise the DNA channel for the initial input image, the masks from the cellpose nuclear segmentation, and finally the masks after further preprocessing e.g. after removing the cells which are in contact with the border of the image.
