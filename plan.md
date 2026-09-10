1. **Fix `init.lua` asset discovery**:
   - The Lua file is mistakenly filtering for `%.gltf$` when it should be loading `%.glb$` per the README.
   - It also completely disables dynamic texture loading, forcing `colormap.png`. Update the `textures` array assignment logic to match what is written in the README (dynamically search for variants, fallback to `<mob>.png`, etc).
2. **Convert the models**:
   - The 3D assets provided in the repository (`models/`) are separated as `.gltf` and `.bin` with a `.png` texture. In Minetest, such models should be unified as a standalone `.glb` to allow proper loading from the Virtual File System without complex local directory path constraints.
   - I will use `npx gltf-pipeline` (or similar) to convert all `.gltf` into `.glb`.
3. **Clean up old assets**:
   - Delete all `.gltf`, `.bin`, and redundant `baseColor_1.png` files from `models/`.
   - Delete the temporary `models/Textures` folder.
4. **Complete pre commit steps**
   - Run tests/validation to ensure no breaking issues.
5. **Submit the change**
