# Computer-vision-assignment-

Q1. Read an image using OpenCV and display it.
# 
def q1():
    image = load_color_image()
    if image is None:
        return

    cv2.imshow("Q1 - Original Image", image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# =
# Q2. Check whether an image was loaded successfully.
# ==
def q2():
    image = cv2.imread(IMAGE_PATH)

    if image is None:
        print("Error: Image could not be loaded.")
    else:
        print("Image loaded successfully.")


# ===
# Q3. Print image height, width, and number of channels.
# =
def q3():
    image = load_color_image()
    if image is None:
        return

    height, width, channels = image.shape
    print("Height:", height)
    print("Width:", width)
    print("Number of channels:", channels)


# ==
# Q4. Calculate and print total number of pixels.
# ===
def q4():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]
    total_pixels = height * width

    print("Total number of pixels:", total_pixels)


# =
# Q5. Print the image data type.
# ==
def q5():
    image = load_color_image()
    if image is None:
        return

    print("Image data type:", image.dtype)


# ===
# Q6. Read an image and save it with a different filename.
# ====
def q6():
    image = load_color_image()
    if image is None:
        return

    output_name = "q6_saved_image.jpg"
    cv2.imwrite(output_name, image)

    print("Image saved as:", output_name)


# ===
# Q7. Read an image directly in grayscale and display it.
# ===
def q7():
    gray = cv2.imread(IMAGE_PATH, cv2.IMREAD_GRAYSCALE)

    if gray is None:
        print("Error: Could not load image.")
        return

    cv2.imshow("Q7 - Grayscale Image", gray)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ===
# Q8. Convert a color image to grayscale using cv2.cvtColor().
# ==
def q8():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    cv2.imshow("Q8 - Grayscale", gray)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ===
# Q9. Display an image using Matplotlib and hide the axis.
# ====
def q9():
    image = load_color_image()
    if image is None:
        return

    image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

    plt.imshow(image_rgb)
    plt.axis("off")
    plt.title("Q9 - Image using Matplotlib")
    plt.show()


# ==
# Q10. Resize an image to 50% width and height.
# ===
def q10():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]

    new_width = width // 2
    new_height = height // 2

    resized = cv2.resize(image, (new_width, new_height))

    cv2.imshow("Q10 - 50% Resized Image", resized)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ====
# Q11. Access and print the pixel at user-provided (x, y).
# =====
def q11():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]

    try:
        x = int(input(f"Enter x coordinate (0 to {width - 1}): "))
        y = int(input(f"Enter y coordinate (0 to {height - 1}): "))

        if 0 <= x < width and 0 <= y < height:
            pixel = image[y, x]
            print(f"Pixel at ({x}, {y}):", pixel)
        else:
            print("Error: Coordinates are outside the image.")
    except ValueError:
        print("Error: Please enter integer coordinates.")


# ===
# Q12. Modify a selected pixel intensity/value and save it.
# ===
def q12():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]

    try:
        x = int(input(f"Enter x coordinate (0 to {width - 1}): "))
        y = int(input(f"Enter y coordinate (0 to {height - 1}): "))

        if 0 <= x < width and 0 <= y < height:
            image[y, x] = [255, 255, 255]

            output_name = "q12_modified_image.jpg"
            cv2.imwrite(output_name, image)

            print(f"Pixel at ({x}, {y}) changed to white.")
            print("Modified image saved as:", output_name)
        else:
            print("Error: Coordinates are outside the image.")
    except ValueError:
        print("Error: Please enter integer coordinates.")


# ==
# Q13. Print B, G, R values at a selected pixel.
# ===
def q13():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]

    try:
        x = int(input(f"Enter x coordinate (0 to {width - 1}): "))
        y = int(input(f"Enter y coordinate (0 to {height - 1}): "))

        if 0 <= x < width and 0 <= y < height:
            B, G, R = image[y, x]

            print("Blue (B):", B)
            print("Green (G):", G)
            print("Red (R):", R)
        else:
            print("Error: Coordinates are outside the image.")
    except ValueError:
        print("Error: Please enter integer coordinates.")


# ===
# Q14. Split a color image into B, G, R channels and display them.
# ==
def q14():
    image = load_color_image()
    if image is None:
        return

    B, G, R = cv2.split(image)

    cv2.imshow("Q14 - Blue Channel", B)
    cv2.imshow("Q14 - Green Channel", G)
    cv2.imshow("Q14 - Red Channel", R)

    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ====
# Q15. Merge three separate channels into one color image.
# =====
def q15():
    image = load_color_image()
    if image is None:
        return

    B, G, R = cv2.split(image)
    merged_image = cv2.merge([B, G, R])

    cv2.imshow("Q15 - Merged Color Image", merged_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ===
# Q16. Calculate and print minimum and maximum grayscale intensity.
# =====
def q16():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    print("Minimum intensity:", np.min(gray))
    print("Maximum intensity:", np.max(gray))



# Q17. Calculate and print mean grayscale intensity.
# =======
def q17():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    print("Mean intensity:", np.mean(gray))


# ===
# Q18. Calculate mean and standard deviation of grayscale image.
# ====
def q18():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    mean_value = np.mean(gray)
    std_value = np.std(gray)

    print("Mean intensity:", mean_value)
    print("Standard deviation:", std_value)


# ====
# Q19. Create a 256x256 grayscale image with intensity 128.
# ======
def q19():
    image = np.full((256, 256), 128, dtype=np.uint8)

    cv2.imshow("Q19 - Constant Intensity 128", image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    cv2.imwrite("q19_constant_128.png", image)
    print("Created 256x256 grayscale image with intensity 128.")


# ===
# Q20. Create and display a grayscale intensity ramp from 0 to 255.
# ==
def q20():
    row = np.arange(256, dtype=np.uint8)
    ramp = np.tile(row, (256, 1))

    cv2.imshow("Q20 - Intensity Ramp 0 to 255", ramp)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    cv2.imwrite("q20_intensity_ramp.png", ramp)
    print("Created grayscale intensity ramp from 0 to 255.")


# ===
# Q21. Convert 8-bit grayscale image to 4-bit quantized image.
# =====
def q21():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # 8-bit values (0-255) -> 4-bit values (0-15)
    quantized = gray // 16

    # Scale back for visible display: 0-15 -> 0-255
    display_image = (quantized * 17).astype(np.uint8)

    cv2.imshow("Q21 - 4-bit Quantized Image", display_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    cv2.imwrite("q21_4bit_quantized.png", display_image)
    print("4-bit quantization completed.")
    print("Quantized intensity levels: 0 to 15")


# ====
# Q22. Convert 8-bit grayscale image to 2-bit quantized image.
# =====
def q22():
    image = load_color_image()
    if image is None:
        return

    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    # 8-bit values (0-255) -> 2-bit values (0-3)
    quantized = gray // 64

    # Scale back for visible display: 0-3 -> 0-255
    display_image = (quantized * 85).astype(np.uint8)

    cv2.imshow("Q22 - 2-bit Quantized Image", display_image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    cv2.imwrite("q22_2bit_quantized.png", display_image)
    print("2-bit quantization completed.")
    print("Quantized intensity levels: 0 to 3")


# ====
# Q23. Downsample an image by factor 2 in width and height.
# ====
def q23():
    image = load_color_image()
    if image is None:
        return

    original_height, original_width = image.shape[:2]

    new_width = original_width // 2
    new_height = original_height // 2

    downsampled = cv2.resize(image, (new_width, new_height))

    print("Original resolution:", original_width, "x", original_height)
    print("New resolution:", new_width, "x", new_height)

    cv2.imshow("Q23 - Downsampled Image", downsampled)
    cv2.waitKey(0)
    cv2.destroyAllWindows()


# ====
# Q24. Crop a rectangular ROI using user-provided coordinates.
# =======
def q24():
    image = load_color_image()
    if image is None:
        return

    height, width = image.shape[:2]

    print("Image size:", width, "x", height)

    try:
        x1 = int(input("Enter x1: "))
        y1 = int(input("Enter y1: "))
        x2 = int(input("Enter x2: "))
        y2 = int(input("Enter y2: "))

        if (
            0 <= x1 < x2 <= width
            and 0 <= y1 < y2 <= height
        ):
            roi = image[y1:y2, x1:x2]

            cv2.imshow("Q24 - Cropped ROI", roi)
            cv2.waitKey(0)
            cv2.destroyAllWindows()

            cv2.imwrite("q24_cropped_roi.jpg", roi)
            print("Cropped ROI saved as: q24_cropped_roi.jpg")
        else:
            print("Error: Invalid coordinates.")
    except ValueError:
        print("Error: Please enter integer coordinates.")


# ===
# Q25. Rotate an image by 90 degrees, display and save it.
# ====
def q25():
    image = load_color_image()
    if image is None:
        return

    rotated = cv2.rotate(image, cv2.ROTATE_90_CLOCKWISE)

    cv2.imshow("Q25 - Rotated 90 Degrees", rotated)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    output_name = "q25_rotated_90.jpg"
    cv2.imwrite(output_name, rotated)

    print("Image rotated by 90 degrees clockwise.")
    print("Saved as:", output_name)


# ============================================================
# MAIN MENU
# ============================================================
def main():
    print("\n==============================================")
    print(" COMPUTER VISION - DAY 1")
    print(" Q1 - Q25 SINGLE PYTHON FILE")
    print("==============================================")

    while True:
        print("\nSelect a question:")
        print("1  - Q1  Read and display image")
        print("2  - Q2  Check image loading")
        print("3  - Q3  Height, width, channels")
        print("4  - Q4  Total pixels")
        print("5  - Q5  Data type")
        print("6  - Q6  Save image")
        print("7  - Q7  Read grayscale")
        print("8  - Q8  Convert to grayscale")
        print("9  - Q9  Display using Matplotlib")
        print("10 - Q10 Resize to 50%")
        print("11 - Q11 Access pixel")
        print("12 - Q12 Modify pixel")
        print("13 - Q13 Print BGR values")
        print("14 - Q14 Split channels")
        print("15 - Q15 Merge channels")
        print("16 - Q16 Min/Max intensity")
        print("17 - Q17 Mean intensity")
        print("18 - Q18 Mean/Standard deviation")
        print("19 - Q19 Constant image")
        print("20 - Q20 Intensity ramp")
        print("21 - Q21 4-bit quantization")
        print("22 - Q22 2-bit quantization")
        print("23 - Q23 Downsampling")
        print("24 - Q24 Crop ROI")
        print("25 - Q25 Rotate 90 degrees")
        print("0  - Exit")

        choice = input("\nEnter question number: ").strip()

        functions = {
            "1": q1, "2": q2, "3": q3, "4": q4, "5": q5,
            "6": q6, "7": q7, "8": q8, "9": q9, "10": q10,
            "11": q11, "12": q12, "13": q13, "14": q14, "15": q15,
            "16": q16, "17": q17, "18": q18, "19": q19, "20": q20,
            "21": q21, "22": q22, "23": q23, "24": q24, "25": q25
        }

        if choice == "0":
            print("Program ended.")
            break
        elif choice in functions:
            print(f"\n--- Running Q{choice} ---")
            functions[choice]()
        else:
            print("Invalid choice. Please enter a number from 0 to 25.")


if __name__ == "__main__":
    main()
