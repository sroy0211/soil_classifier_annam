✅ Explanation: How the Architecture Processes the Image

The annotated architecture diagram present in **Architecture.jpg** in docs folder represents the full workflow of the soil classification model. Below is a detailed explanation of each block:

🔷 Input Image

Raw soil photographs are fed into the model.

These images vary in size and lighting conditions, so they must be standardized.

🔹 Image Transformations

Resize: Converts each image to 224×224 pixels to match the input size of EfficientNet-B0.

Normalize: Adjusts the color channels to match the ImageNet pre-trained model distribution.

Augmentation: Adds randomness (flips, rotation, jitter) to help generalize the model.

🟩 EfficientNet-B0 (Pre-trained CNN)

A state-of-the-art convolutional neural network trained on ImageNet.

Used for feature extraction, identifying textures, edges, and patterns in soil images.

Only the final classification layer is customized.

🟦 Global Average Pooling

Reduces feature maps to a lower-dimensional vector by averaging each channel.

Makes the model more robust to spatial translations (e.g., where soil patterns appear in the image).

🟥 Output Layer

A fully connected (linear) layer outputs class scores for:

Alluvial soil

Black soil

Clay soil

Red soil

Softmax activation is applied implicitly to generate a probability distribution across classes.

🟪 Training

Loss: CrossEntropyLoss compares predictions to ground-truth labels.

Optimizer: AdamW updates model weights.

Training loop uses early stopping based on the minimum F1-score across classes to ensure balanced performance.

🟪 Evaluation

Computes F1-score per class.

Final score = minimum F1 (encourages performance across all soil types).

🟩 Results

Final predictions are saved to a CSV file.

Includes image ID and predicted soil type.

Used for submission and ranking.
