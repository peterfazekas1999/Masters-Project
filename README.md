# LSTM-GAN-Prototype
The random perturb folder contains the verification of the theoretical proposed bound. It simulates random perturbations and finds the radius required for a specific proportion of misclassification. differential.py calculates the hessian and 3rd order partial derivative tensor for a feedforward function as well as calculating the constants needed for the bound in the theorem. In this case an example of a 1 hidden layer ANN separatin 2 sets of points in a 2 dimensional plane has been used for demonstration purposes.
<br/>
The saved model is too large to upload on GitHub but the code includes the training and the saving of the models.
<br />
<br />
Run the exogen-notebook.ipynb to train the GAN and the LSTM classifier and save the trained model.
<br />
<br />
Run BATMAN-GAN.ipynb to generate artificial exoplanet-like light curves using the trained GAN and the BATMAN package.

This is a prototype model for exoplanet transit curve generation. The generator uses a Fully connected layer which takes in a random sequence of data and outputs a lightcurve-like graph when plotted. The discriminator consists of LSTM layers stacked on top of each other. This is only a prototype model for my Masters research project, in the future I plan to improve the model architecture to generate more realistic "exoplanets". Below I provide examples of how well the GAN performs against a trained LSTM classifier.

The Generator seems to capture the noise characteristics of the data really well, but not the periodic dips that occurs during the transit of a planet in front of the host star. A further improvement to the model is to use an existing python package to artificially insert these "dips" on a GAN generated image and then test how a pre-existing classifier reacts to these artificially crafted planets.

The data from Kaggle can be downloaded from this link: https://www.kaggle.com/keplersmachines/kepler-labelled-time-series-data

As a reference, these are real transit curve for an exoplanet. <br />
<img src="https://github.com/peterfazekas1999/LSTM-GAN-Prototype/blob/master/GAN-LSTM%20generated/GAN_3_real.jpg" width ="300">
<img src="https://github.com/peterfazekas1999/LSTM-GAN-Prototype/blob/master/GAN-LSTM%20generated/real_curve.png" width ="300">

The 2 images below are examples from the GAN
<br />

The first image is the output of the GAN, the second image is the same output after artificially inserting exoplanet transits.<br />
<img src="https://github.com/peterfazekas1999/LSTM-GAN-Prototype/blob/master/GAN_output.png" width ="300">
<img src="https://github.com/peterfazekas1999/LSTM-GAN-Prototype/blob/master/GAN_BTM.png" width ="300">

Below is the performance of the classifier trained on the Kaggle dataset, the output is 0 (No exoplanet) and 1 (if there is an exoplanet). I have used the model to make a prediction on 5 generated images.
(Prediction 2) refers to the images above. Without BATMAN, the classifier is not fooled. However after inserting artificial transits the classifier outputs 0.97, it is very confident that the lightcurve contains an exoplanet.
<img src="https://github.com/peterfazekas1999/LSTM-GAN-Prototype/blob/master/prediction.png" width ="1000">
<br />
<br />
Picking 2 random axes and creating a mesh allows the visualization of slices of higher dimensional decision boundaries. The images below show what the 2-dimensional slices of these boundaries look like.
<br />
<br />
<img src="https://github.com/peterfazekas1999/Masters-Project/blob/master/exo_decisionB%20results/exobound_17.jpg" width ="500">
<img src="https://github.com/peterfazekas1999/Masters-Project/blob/master/exo_decisionB%20results/exobound_25.jpg" width ="500">
