# TP : Gestion des produits avec Spring Boot, Spring Data JPA et H2

## 1. Introduction

Ce projet consiste à développer une application web de gestion des produits en utilisant le framework Spring Boot.

L'objectif est de mettre en place une application permettant d'effectuer les opérations CRUD (Create, Read, Update, Delete) sur des produits à l'aide de Spring Data JPA et d'une base de données H2.

Ce travail pratique est réalisé en suivant la vidéo de démonstration :

**First Demo :** https://www.youtube.com/watch?v=UXs39oVoaSs

## 2. Objectifs du TP

- Créer un projet Spring Boot avec Spring Initializr.
- Configurer les dépendances nécessaires.
- Créer une entité JPA Product.
- Configurer la base de données H2.
- Utiliser Spring Data JPA pour accéder aux données.
- Développer les opérations CRUD.
- Tester les fonctionnalités de gestion des produits.

## 3. Environnement et technologies utilisés

Les technologies utilisées dans ce projet sont :

| Technologie | Description |
|---|---|
| Java | Langage de programmation |
| IntelliJ IDEA Ultimate | Environnement de développement |
| Spring Boot | Framework de développement |
| Spring Web | Création des services web REST |
| Spring Data JPA | Gestion de la persistance des données |
| Hibernate | Mapping objet-relationnel (ORM) |
| H2 Database | Base de données relationnelle |
| Lombok | Réduction du code répétitif |
| Maven | Gestion des dépendances |

## 4. Création du projet Spring Boot

Le projet est créé à l'aide de Spring Initializr avec les paramètres suivants :

- Project : Maven
- Language : Java
- Packaging : Jar
- Java : version compatible avec Spring Boot

### Dépendances ajoutées

- Spring Web
- Spring Data JPA
- H2 Database
- Lombok

## 5. Création de l'entité Product

L'entité `Product` représente un produit dans la base de données.

Elle contient les attributs suivants :

| Attribut | Type | Description |
|---|---|---|
| id | Long | Identifiant unique du produit |
| name | String | Nom du produit |
| price | double | Prix du produit |
| quantity | int | Quantité disponible |

### Code de l'entité Product

```java
package ma.tp.productmvc.entities;

import jakarta.persistence.*;
import lombok.*;

@Entity
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;
    private double price;
    private int quantity;
}
```

**Explication :**

- `@Entity` : indique que la classe est une entité JPA.
- `@Id` : définit la clé primaire.
- `@GeneratedValue` : permet de générer automatiquement l'identifiant.
- `@Data` : génère les getters, setters et autres méthodes.
- `@NoArgsConstructor` : crée un constructeur sans paramètres.
- `@AllArgsConstructor` : crée un constructeur avec tous les paramètres.

## 6. Configuration de la base de données H2

La configuration de la base de données est effectuée dans le fichier `application.properties`.

```properties
spring.application.name=product-mvc

spring.datasource.url=jdbc:h2:mem:products-db
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

spring.h2.console.enabled=true
spring.h2.console.path=/h2-console
```

**Explication :**

- `spring.datasource.url` : définit l'adresse de la base de données.
- `spring.datasource.username` : définit l'utilisateur.
- `spring.datasource.password` : définit le mot de passe.
- `spring.jpa.hibernate.ddl-auto` : configure la génération du schéma de la base de données.
- `spring.jpa.show-sql` : affiche les requêtes SQL dans la console.
- `spring.h2.console.enabled` : active la console H2.

La base de données utilisée est une base en mémoire. Les données sont donc supprimées à l'arrêt de l'application.

## 7. Création de l'interface Repository

Spring Data JPA permet de gérer les opérations sur les produits sans écrire manuellement les requêtes SQL de base.

```java
package ma.tp.productmvc.repositories;

import ma.tp.productmvc.entities.Product;
import org.springframework.data.jpa.repository.JpaRepository;

public interface ProductRepository extends JpaRepository<Product, Long> {
}
```

**Explication :**

L'interface `ProductRepository` hérite de `JpaRepository`, ce qui permet d'utiliser automatiquement plusieurs méthodes :

- `save()` : ajouter ou modifier un produit.
- `findAll()` : consulter tous les produits.
- `findById()` : rechercher un produit par son identifiant.
- `deleteById()` : supprimer un produit.

## 8. Les opérations CRUD

L'application permet de réaliser les opérations suivantes :

### 8.1 Ajouter des produits

Permet d'enregistrer un nouveau produit dans la base de données.

### 8.2 Consulter tous les produits

Permet d'afficher la liste de tous les produits enregistrés.

### 8.3 Consulter un produit

Permet de rechercher un produit à partir de son identifiant.

### 8.4 Chercher des produits

Permet de rechercher des produits selon un critère, comme leur nom ou leur prix, selon les méthodes de recherche implémentées.

### 8.5 Mettre à jour un produit

Permet de modifier les informations d'un produit existant.

### 8.6 Supprimer un produit

Permet de supprimer un produit de la base de données à partir de son identifiant.

## 9. Tests et vérification

Les différentes fonctionnalités de l'application peuvent être testées à l'aide de Postman ou d'un autre client HTTP.

Les tests portent sur :

- L'ajout de nouveaux produits.
- L'affichage de la liste des produits.
- La consultation d'un produit par son identifiant.
- La recherche de produits.
- La modification des informations d'un produit.
- La suppression d'un produit.

**Remarque :** Les captures d'écran des tests peuvent être ajoutées ici pour illustrer les résultats obtenus.

## 10. Conclusion

Ce travail pratique m'a permis de découvrir le développement d'une application de gestion des produits avec Spring Boot.

J'ai appris à créer une entité JPA, configurer une base de données H2 et utiliser Spring Data JPA pour effectuer les opérations CRUD.

Ce projet m'a également permis de mieux comprendre le fonctionnement de la persistance des données et le développement d'applications web avec Spring Boot.

## 11. Repository GitHub

**Nom du projet :** Product MVC

**Lien GitHub :** https://github.com/sihamloukch/product-mvc

