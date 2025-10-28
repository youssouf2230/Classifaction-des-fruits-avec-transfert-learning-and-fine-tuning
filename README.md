# Classification des Fruits avec Transfer Learning et Fine-Tuning
## Description du projet

Ce projet consiste à construire un modèle de classification d’images de fruits à partir du dataset Fruits-360 (version original size).
L’objectif est d’identifier automatiquement le type de fruit à partir d’une image, en exploitant la puissance du Transfer Learning et du Fine-Tuning pour obtenir de hautes performances avec un temps d’entraînement réduit.

## Objectifs

Utiliser un modèle pré-entraîné (comme MobileNetV2, VGG16 ou ResNet50) sur ImageNet.

Adapter ce modèle à notre dataset de fruits via transfer learning.

Améliorer la précision grâce au fine-tuning (déblocage des couches profondes).

Comparer les performances entre le modèle de base et le modèle ajusté.

Visualiser les prédictions du modèle sur des images du jeu de test.

## Préparation des données

Le dataset Fruits-360 Original Size contient plus de 60 000 images réparties dans plus de 100 classes.
Cependant, certaines classes représentent en réalité des variantes du même fruit (ex. Apple Golden 1, Apple Golden 2, Apple Golden 3).
Pour simplifier et rendre la classification plus cohérente :

Les classes similaires ont été regroupées sous un même label général (ex. apple, banana, orange).

Les images ont été redimensionnées à 64×64 pixels.

Des augmentations d’images ont été appliquées : rotation, zoom, décalage, retournement horizontal, etc.

## Modélisation

Transfer Learning :

Chargement d’un modèle pré-entraîné MobileNetV2 avec poids imagenet.

Gel des couches convolutives pour utiliser les caractéristiques déjà apprises.

Ajout de couches denses personnalisées pour la classification des fruits.

Fine-Tuning :

Déblocage partiel des dernières couches du modèle pour un apprentissage plus précis.

Ré-entraînement sur un nombre réduit d’époques (≈ 5) avec un taux d’apprentissage plus faible.

Résultat : performances proches du modèle complet, mais avec beaucoup moins de calculs.

## Résultats

Nombre de classes : après regroupement, environ 40 catégories principales.

Performance : le modèle fine-tuné atteint presque la même précision que le modèle complet après seulement 5 époques.

Les validations du modèle pré-entraîné et fine-tuné montrent des performances très proches.

Visualisation : affichage de prédictions aléatoires sur 20 images du jeu de test avec étiquettes réelles et prédites.

## Points clés du projet

Utilisation de Transfer Learning pour réduire le temps d’entraînement.

Application de Fine-Tuning pour ajuster le modèle à la spécificité du dataset.

Nettoyage et regroupement intelligent des classes pour améliorer la cohérence des labels.

Pipeline complet : préparation → entraînement → évaluation → visualisation.

## Technologies utilisées

Python 3

TensorFlow / Keras

NumPy, Matplotlib, Pandas

Kaggle API (pour le téléchargement du dataset)
